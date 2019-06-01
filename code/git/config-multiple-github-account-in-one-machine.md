# Config multiple github accounts on single machine

I have 2 github accounts, personal account and working account. So I need config
to add identification in 1 computer.

* Step 1: Generate new ssh key
```sh
ssh-keygen -t rsa -C “your-email-address”
```

This command will show:

```
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/your_username/.ssh/id_rsa):
```

You should enter company name, for example: `id_rsa_sun`. And **Make sure you don’t override id_rsa as this is your existing key for your original account.**

Add this new key to ssh to ssh-agent: `ssh-add -K ~/.ssh/id_rsa_sun`

Add `~/.ssh/config` file like this:

```sh
Host github.com-sun
  IdentityFile ~/.ssh/id_rsa_sun
  User git
  Hostname github.com
```

* Step 2: Add this new key to Github

    + Copy content of `~/.ssh/id_rsa_sun.pub`
    + Add new SSH key in [setting page](https://github.com/settings/keys)


* Step 3: Change remote of git repo

    + Cd to working repo and type `git config -e`
    + Edit url of the remote, for example:

    ```sh
    [remote "upstream"]
      url = git@github.com-sun:tuantv-0547/hypebid.git
      fetch = +refs/heads/*:refs/remotes/upstream/*
    ```

Done. Now you can add commit and push. :D
