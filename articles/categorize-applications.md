# Organizing /Applications folder in macOS

I struggle sometimes with hundreds of apps installed in my Applications folder.

For frequently-used apps, Alfred is my best friend.
For most of the time, I can open the app I want within a few keystrokes.

But for other apps I use occationaly, it is hard to remember the name every time, so I can only skim through the Applications folder to find the app I need. But it's hard to get the functionality of each app just by looking through the icons and names, it is like find a needle in a haystack. 

Although you can always group or sort the apps to help you find what you need, like the tip shown [here](https://eshop.macsales.com/blog/40569-quick-tip-arrange-your-mac-apps-by-category-in-finder/) to group them by default category, I still feel it's not enough for massive apps since the default categories are too broad.

So I decided to categorize them further myself, similar idea to how iOS does it in the App Library.

I came across this blog post by [Jeff](http://blog.hyperjeff.net/?p=44) where he shared his way of categorizing the /Applications folder. As far as I appreciate the idea behind the post, there is some problems if you do exactly as he did as the time of writing.

The reason is Apple would not allow you move around stock apps(see picture below). 

![](../output/pics/Error_move_settings.png)

Even some third-party apps might not work properly if you move them. For example, applescript like the following would break if you move iTerm away from /Applications folder (This is the applescript that you can change default terminal to iTerm in Alfred's preferences):

```
on alfred_script(q)
	tell application "iTerm"
		activate
		tell current window
			create tab with default profile
			tell current session
				write text q
			end tell
		end tell
	end tell
end alfred_script
```

Moreover, package installers(.pkg, not .dmg) would by default put the app to /Applications folder, and there might be problem if move them according to a comment in this [post](https://superuser.com/questions/76094/organizing-the-mac-os-x-applications-directory).

All this tells us it is better to leave as it is in the /Applications folder. So a good way to deal with this is to create a new folder and put the aliases of all the apps in the new folder. I use '~/Applications', and create alias are as simple as just dragging the apps to the new folder. An easy way to start - You can borrow the categories from the default categories groups using the tips [here](https://eshop.macsales.com/blog/40569-quick-tip-arrange-your-mac-apps-by-category-in-finder/).

![](../output/pics/finder_info.png)

⌘ + J in the /Applications folder, group the apps by the default categories, and then move the apps in each group to different subfolders in the new folder. The groups might be too broad. Then you can start from there to modify the categories to your own preference.

Okay, now app alias are in different subfolders, we have the confidence to find the non-frequently-used apps more easily. But what if there is a new app installed? What if we want to remove an app? To keep the system running, an important thing is to keep the alias in the ~/Applications folder up-to-date.

For this, you can use Hazel or some automation tools (Automator, Keyboard Maestro, or other folder watcher) to script the process of creating alias and moving them to ~/Applications. Here is an example of how to do it with Hazel for the new app installed: 

![](../output/pics/Hazel_rule.png)

Now everytime there is a new app installed, Hazel will create an alias in the ~/Applications folder. Just like put it in app inbox, I can review the app and decide which category it belongs to or just toss it to keep the total number reasonable. Unfortunately, with Hazel, I don't find a good way to automatically remove the correspdonding alias when the app is removed. But I have made a [keyboard maestro macro](../output/pics/Update-alias-when-trashing-apps.kmmacros) to do this, inspired by this [post](https://forum.keyboardmaestro.com/t/solved-find-specific-files-inside-folders-and-sub-folders-and-then-copy-them/33042).

![](../output/pics/km_macro.png)

I did this because it bothers me sometimes, when I want to find a specific app but I forgot the name, and finding it without hierarchy is difficult. At the end of the day, you can always delete the apps you don't use to limit the number of apps. Then the flat structure of the /Applications folder is not a problem anymore.

If there aren't many apps at the first place or even there are that it does not bother you, there is no need to do this. Just as the saying goes, if it ain't broke, don't fix it.