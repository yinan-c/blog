# How to setup SSH keys for GitHub and remote servers?

## Why using SSH keys?

- When connecting a remote server, it may be preferable to use SSH keys, which provide a more secure form of remote communication.
- SSH keys make it possible to securely connect to servers without having to type password every time.

## Method 1: Using ssh-keygen

### Generate the SSH keys on your local machine

On your local machine terminal, run: 

`ssh-keygen -t rsa -b 2048`

You will be prompted to choose a passphrase for the keys as following. Please be sure to enter a passphrase. This is the password that will protect your keys. It can be a sentence with spaces between the words. Be sure to use a combination of lower and upper case letters, numbers and punctuation marks.

```
Generating public/private rsa key pair.
Enter file in which to save the key (/home/localuser/.ssh/id_rsa):
Enter passphrase (empty for no passphrase): 
Enter your passphrase here
```
### Copy the public key to the remote server or GitHub 

- On your local machine, run following command to transfer the generated public key to remote server:
`scp ~/.ssh/id_rsa.pub username@remote.server:~/.ssh/temp.pub`

- SSH to your remote server,
`ssh username@remote.server`

- On your remote server, append the public key to `~/.ssh/authorized_keys`:
```
cat ~/.ssh/temp.pub >> .ssh/authorized_keys
chmod 600 .ssh/authorized_keys && rm .ssh/temp.pub
```


- Now connecting with SSH from your local machine to remote server will now ask for a passphrase instead of a password. 

### Activate the SSH agent on your local machine
You will now need to set up the SSH agent on your local computer. The SSH agent will remember your passphrase and forward your key on, securely, to your remote server.

Use `ssh-add` to add your passphrase to the SSH agent for the current login session. 
On your local machine: run `ssh-add` and you will be prompted to enter your passphrase you just set up.

Within the same login session, you can now ssh to your remote server without entering the passphrase or password.

### Sign your commits with SSH keys on GitHub

#### Configure Git 

We need to configure Git to let it know who we are by setting up our name and email address.
    
```
git config --global user.name "Your Name"
git config --global user.email "Your Email"
```

Then we need to eanble GPG signing for Git commits and the format of the signature will be SSH keys.

```
git config --global commit.gpgsign true
git config --global gpg.format ssh
```

Then we want to tell Git to use the key we just generated locally and uploaded to GitHub.

List your public SSH keys with `ssh-add -L` and copy the key you just generated. 

Then set our signing key in Git to the key we just copied.

```
git config --global user.signingkey <paste your key here>
```

Your commits will now be signed with your SSH key. you can test it by making a commit and checking the signature with `git log --show-signature`.

#### Add SSH key to GitHub

To sign your pushed commits on GitHub so that your commits will be marked as verified, you need to add your public SSH key to GitHub.

Login to [GitHub SSH keys](https://github.com/settings/keys), copy and Paste your public key to both Authentication Keys and Signing keys. 

## Method 2: using 1Password SSH agent

[1Password](https://1password.com/) is a powerful password manager with easy-to-use auto-fill functionalities. I use it to store any sensitive documents and login credentials, to generate random passwords for all my online accounts.  (no affiliation or sponsorship, just a happy user)

> For students, you can get 1-year 1Password subscription via the [GitHub Student Developer Pack - GitHub Education](https://education.github.com/pack).

As an alternative method, you can generate SSH keys using 1Password or import your SSH keys from your local file (e.g. ~/.ssh/id_rsa). 

1Password will generate a public key automatically and store the public and private key-pair in your 1Password vault.

Then what you need to do is quite similar with a few more steps:
As tested in 1Password 8 in July 2023, these instructions will be automatically prompted in the 1Password client after you generate or import SSH keys, setting up SSH keys with 1Password is quite straightforward.

- Append the public key to ~/.ssh/authorized_keys or to upload your public key to GitHub.
- Turn on the 1Password SSH agent.
- Configure your SSH or Git client, similar to Method 1, but 1Password will automatically modify the configuration for you. (Be sure to backup your `~/.ssh/config` and `~/gitconfig` file before you let 1Password overwrite them.)
- Run any `ssh` or `git` and authorize the SSH request prompted by 1Password.

Please refer to [official document](https://developer.1password.com/docs/ssh/get-started) for a detailed step-by-step documentation.

## References and further reading
[1] [How do I setup SSH keys? - Minnesota Supercomputing Institute](https://www.msi.umn.edu/support/faq/how-do-i-setup-ssh-keys)

[2] [SSH & Git - 1Password docs](https://developer.1password.com/docs/ssh/get-started)

[3] [Sign Git commits with SSH - 1Password docs](https://developer.1password.com/docs/ssh/git-commit-signing)

[4] [How to Sign git Commits with an SSH key - Jack Wallen](https://thenewstack.io/how-to-sign-git-commits-with-an-ssh-key/)

