# Git / GitHub workshop

The goal of this workshop is to explain how to use Git / GitHub correctly

## Set up git

- [Install Git](https://git-scm.com/downloads)
- Set up global username:
    - `git config --global user.name "yourUsername"`
    - check your global username : 
        - `git config --global user.name`
- Set up global email:
    - `git config --global user.email "your@email.com"`
    - check your global username : 
        - `git config --global user.email`

## Create a SSH key

- checking for existing key:
    - `ls -al ~/.ssh`
- create a new key:
    - `ssh-keygen -t rsa -b 4096 -C "your@email.com"`
    - **`Enter a file in which to save the key (/Users/you/.ssh/id_rsa):`** `[Press enter]`
    - **`Enter passphrase (empty for no passphrase):`** `[Type a passphrase]`
    - **`Enter same passphrase again:`** `[Type passphrase again]`
- adding your key to ssh-agent:
    - `eval "$(ssh-agent -s)"` return your Agent pid
    - On Mac Sierra 10.12.2 or later :
        ```bash
        Host *
            AddKeysToAgent yes
            UseKeychain yes
            IdentityFile ~/.ssh/id_rsa
        ```
        - `ssh-add -K ~/.ssh/id_rsa`
    - On Windows:
        - `ssh-add ~/.ssh/id_rsa`
- adding your key to your GitHub account:
    - On Mac:
        - `pbcopy < ~/.ssh/id_rsa.pub`
    - On Windows:
        - `clip < ~/.ssh/id_rsa.pub`
    - Or just `cat ~/.ssh/id_rsa.pub` and manually copy the content
    - Go to your GitHub account:
        - Settings > SSH and GPG keys > New SSH key
        - Add a title: `Example: Personnal computer SSH key`
        - Paste your public key
        - Add your SSH key