# Tailscale 访问内网特定端口

搬家之后，家里的宽带从原来的 Virgin Media 1000 Mbps 下行100 Mbps 上行换到了 Hyperoptic 1000 Mbps 上下对等的光纤，价格都在37英镑每月，原以为是一次各方面的升级，结果却发现 Hyperoptic 并没有提供公网 ip（VM 提供公网 ipv4 在套餐内），如果要开通则需额外付5英镑每月。

原本一些运行在 nas 上的服务通过 OpenVPN 提供自组网内访问，但是考虑到安全问题，我并没有把 VPS 加入自组网，如果确实需要访问 nas 中的特定服务则通过路由器端口映射和防火墙提供给 VPS 访问。没有了公网 ip 之后，无法将服务端口映射开放，只能另寻其他解决方案。

## Tailscale 的安全配置

之前在用 OpenVPN 的时候，也尝试过 Tailscale、Netbird 等自组网，现在为了让 VPS 也能访问到 nas 上的特定服务就必须要把 VPS 也加入到 Tailscale 网络，但是我又不想要 VPS 能够访问 Tailscale 网内的所有设备所有服务，就需要限制 VPS 只允许访问内网特定设备的特定端口 - 通过设定 ACL 规则。

这里贴出我的部分配置方案，去除了默认 grants 中允许所有连接的配置，加上了两条规则，仅允许 VPS 访问 NAS 的13333端口以及其他所有设备和 nas 互联。

```
{
	// Define the tags which can be applied to devices and by which users.
	"tagOwners": {
		"tag:nas": ["autogroup:admin"],
		"tag:vps": ["autogroup:admin"],
	},

	// Define grants that govern access for users, groups, autogroups, tags,
	// Tailscale IP addresses, and subnet ranges.
	//"grants": [
	// Allow all connections.
	// Comment this section out if you want to define specific restrictions.
	//	{"src": ["*"], "dst": ["*"], "ip": ["*"]},
	//],

	// Define users and devices that can use Tailscale SSH.
	"ssh": [
		// Allow all users to SSH into their own devices in check mode.
		// Comment this section out if you want to define specific restrictions.
		{
			"action": "check",
			"src":    ["autogroup:member"],
			"dst":    ["autogroup:self"],
			"users":  ["autogroup:nonroot", "root"],
		},
	],
	// 定义访问控制规则
	"acls": [
		// 规则一：允许所有设备互相访问所有端口。
		// "autogroup:member" 代表 Tailscale 网络中的所有用户及其设备。
		{
			"action": "accept",
			"src":    ["autogroup:member"],
			"dst":    ["autogroup:member:*", "tag:nas:*"],
		},

		// 规则二：仅允许 VPS 访问 NAS 的13333端口。
		{
			"action": "accept",
			"src":    ["tag:vps"],
			"dst":    ["tag:nas:13333"],
		},
	],

	// (可选) 添加测试以验证规则是否按预期工作

	"tests": [
		{
			"src":    "tag:vps",
			"accept": ["tag:nas:13333"], // 应该允许访问 13333 端口
			"deny":   ["tag:nas:5000"], // 应该拒绝访问 5000 端口
		}
	],
}
```

配置完成后，如果测试成功则会正常保存配置文件，接下来回到管理设备页面为 nas 和 vps 分别打上标签即可。

另外我发现群晖使用 tailscale 的时候似乎无法通过 tailscale ip 来 ping 内网内的其他设备。

```
sudo ping 100.xx.xx.xxx # 这条会失败

sudo tailscale ping 100.xx.xx.xx # tailscale ping 却能成功
pong from (vps)xxx via 173.xxx.xxx.xxx:xxxxx in 87ms
```

似乎和[这个 bug](https://github.com/tailscale/tailscale/issues/1995) 有关。
