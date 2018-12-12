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

----

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

----

## Basics commands

### Create / clone a repository

- `git init`: create a new local repository
- `git remote add origin <github repository>`: connect your local repo to your distant repo
- `git clone`: clone your distant repo to a local folder

### Interract with files

- `git status | gst` : show only the files with modifications
- `git add | ga` :
    - `git add <file>` : Add a specific file
    - `git add . | ga .` : Add all files with modifications
-  `git commit | gc` :
    - `git commit -m "commit message" | gc -m "commit message"` : commit your file with an informative message
- `git reset` :  reset all or specific files yiu have commited
- `git stash` : stock your changing file in a different place, so you can recover your changes in another branch
    - `git stash list` : display a list of your stashes
    - `git stash apply stash@{$}` : Recove your stash in your current branch

### Send and recove versions

- `git pull / git pull origin <branch> | gl` :
    - `git pull | gl` : default pull command, like `git pull origin master`. It'll recove the version of the code in the `master` branch
    - `git pull origin <specific branch>` : It'll recove the version of the code in a specific branch

- `git push / git push origin <branch> | gp` :
     - `git push | gp` : default push command, like `git push origin master`. It'll send the version of the code in the `master` branch
    - `git push origin <specific branch>` : It'll send the version of the code in a specific branch

### Working with branches

- `git checkout <branch> | gco <branch>` : change your current branch
    - `git checkout -b <branch> | gco -b <branch>` : create a new branch and change to it
- `git branch` :  list all the branches
    - `git branch -d <branch>` : delete a specific branch

----

### Sources

- [GitHub Help](https://help.github.com/)
- [Basic Git commands](https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html)

----

### TP

- Fork ce répo
- Créer une branche avec son pseudo et se mettre sur cette branche
- Ajouter une balise `a` avec son nom, pseudo et lien github, comme ceci:

```HTML
<a href="https://github.com/blyndusk" title="blyndusk's github account">Alexandre Delaloy (blyndusk)</a>
```

- créer une pull request avec vos modifications situé sur votre branche
- Envoyer la pull request

----

- Sémantique de versioning
- Gestion de projet Github