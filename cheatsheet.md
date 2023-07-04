# Common Commands using git

## Commit History

##### Show all commits, starting with the newest

```bash
git log
```

##### Commit history of specific file

```bash
git log -p <file_name>

# EXAMPLE
git log -p README.md
```

##### Commit history by user

```bash
git blame <file_name>

#Example
git blame README.md
```

## Branches

##### List all local branches

```bash
git branch
```

##### List all local and remote branches

```bash
git branch -av
```

##### Switch to an existing branch

```bash
git checkout <branch_name>

# Example
git checkout szabolcsthedeveloper/testBranchName
```

##### Create a new branch

```bash
git checkout -b <brach_name>

# Example
git checkout -b szabolcsthedeveloper/myNewBranchName
```

##### Delete the local branch

```bash
git branch -d <branch_name>

# Example
git branch -d szabolcsthedeveloper/myNewBranchName

## Force delete if not merged
git branch -D szabolcsthedeveloper/myNewBranchName
```

##### Delete remote/origin branch

```bash
git push origin --delete <branch_name>

# Example
git push origin --delete szabolcsthedeveloper/myNewBranchName
```

## Pull and Push


##### Get the latest from remote

pull: gets latest pushed by someone to the branch

```bash
git pull
```

##### Push local changes

push: push local changes to the remote branch

```bash
git push -u origin <branch_name>

# Example
git push -u origin szabolcsthedeveloper/myNewBranchName
```

# Git Init

- Create the directory 
- Change to directory
- Initialize the directory with git and check for hiden folders in the directory


`git init`, to initiate the current directory to connect to the version controlling system or any git server

```bash
mkdir learn-git/
cd learn-git/
git init
```

> O/P : Initialized empty Git repository in `learn-git` directory

- After initializing the repository, it will create the hidden folder in the directory `/home/user/current-path/learn-git`.
- To view hidden fine in direct `Ctrl + H`
- Directory file structure looks like this

```bash
---
root
    branch/
    config
    description
    HEAD
    hooks/
        applypatch-msg.sample
        commit-msg.sample
        fsmonitor-watchman.sample
        post-update.sample
        pre-applypatch.sample
        pre-commit.sample
        prepare-commit-msg.sample
        pre-push.sample
        pre-rebase.sample
        pre-receive.sample
        update.sample
    info/
        exclude
    objects/
        info/
        pack/
    refs/
        heads/
        tags/
```

# Committing files

## Status

```bash
git status
```

## Git Add

```bash
git add .

# OR

git add --all

# OR

git add hello-world.js

# OR

git add dir/
```

## Check status

```bash
git status
```

## Commit

```bash
git commit -am "hello world changes"
```

`-am` : All commits with message

## Push

```bash
git push -u origin branchName

# OR

git push # pushes the current branch to the configured upstream
```

# Remove the last commit/commits using Reset

## Steps to remove the last commit/commits

#### **Step 1** Checkout to master

```bash
git checkout master
```

> Note: This could be done in any branch. For this example, the *master* branch is used.

#### **Step 2** -  Get the commits history

```bash
git log
```

You will end up with a list of commits that you made as follows.

![logs](https://user-images.githubusercontent.com/22785263/47548190-d2dc6580-d915-11e8-8591-c470511ddae0.PNG)

#### Step 3 - Reset

**Step 3.1** - Copy the commit-hash that you want to reset

All the commits that top of the selected commit-hash (not including the entered commit-hash), will be deleted.

**Step 3.2** - Hard reset to go back to the early stage

```bash
git reset <commit-hash> --hard
```

#### Step 3 - Force push to the repository

```bash
git push <remote> master --force
```

`<remote>` can be `origin` is the default.

> NOTE: Be careful when removing the previous commits, there is no going back once you did these changes.


# Setup git push with SSH

## Generate SSH KEY with ssh-keygen

```bash
ssh-keygen -t rsa -C "your_github_email@example.com"
```

> Note : In local machines we may have multiple ssh keys, better to create the specific rsa. 
> Example : Enter file in which to save the key `(/home/ubuntu/.ssh/id_rsa): /home/ubuntu/.ssh/github_rsa`

```bash
O/P:

Generating public/private rsa key pair.
Enter file in which to save the key (/home/ubuntu/.ssh/id_rsa): /home/ubuntu/.ssh/github_rsa
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/ubuntu/.ssh/github_rsa.
Your public key has been saved in /home/ubuntu/.ssh/github_rsa.pub.
The key fingerprint is:
SHA256:vddx6bSnZdfSM0/6pImd5l+yiycMZRMetgp70NuCcRcM *******@outlook.com
The key's randomart image is:
+---[RSA 2048]----+
|  .. .           |
|  .Eo .          |
| o....           |
|.oo..    .       |
|=.*.    T .      |
| *.+       . .   |
| ..o.. .  . ..B. |
| .+.. o oo .=@+o |
|  +o o. oo..=@J  |
+----[SHA256]-----+
```

## Github SSH connection setup

### 1. Copy the ssh from local machine

```bash
 cat /home/ubuntu/.ssh/github_rsa.pub
```

> O/P
> ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC/iLoHDq+6Bz5m5ED1TezxtCeW4U7eZueEqFX2eMo/BRQLVLzIMP7YyiYBR0xX57MgQ4cVodJV8pM0PYrSGSI1lQ5POSMrY4RDrH+KCVbLpifZAjaI94IKJtjnRm9eynk11g9DCg3z+OlxXmBBs1AO/zzqBXBoekfU753bD4u1yhycHiq6Iis9B2FHbV1Yov9ofswnZxh/xX7gXghLo4bdjpwfgDCRlUl4VUf7AeMY3ACwYsiEs1P6R0d1SUITgkP8D6pjmaxbroWLex43wkUxuS+nKJ9/kw7AmWnupBrUi0gfYzNwJI55vkOyhCF7 ********@outlook.com

### 2. Go to github [account settings](https://github.com/settings/keys) page

[![Github Settings](../images/git_settings_ssh_keys.png)](https://github.com/settings/keys)

### 3. Click on [![New SSH key](../images/new_ssh_key.png)](https://github.com/settings/ssh/new)

### 4. Add title and paste the copied ssh key from the local

### 5. Test SSH

```bash
ssh -T git@github.com
```

> O/P
> The authenticity of host 'github.com (192.30.253.113)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'github.com,192.30.253.113' (RSA) to the list of known hosts.
Hi szabolcsthedeveloper! You've successfully authenticated, but GitHub does not provide shell access.

### 6. Update the Remote URL of the repository with the ssh url in place of https

- Copy the url from the ![clone repository](../images/clone_repo.png) button with ssh

- Copy Clone with ssh URL - Clock *Use SSH* as in first screenshot

![click_use_ssh](../images/click_use_ssh.png) ![copy_ssh_url](../images/copy_ssh_url.png)

```bash
 git remote set-url origin git@github.com:szabolcsthedeveloper/Git-Mastery.git
```

### 7. Test pushing with ssh

```bash
git add --all

git commit -am "testing the changes"

git push -u origin master
```

*DONE with Github*

# Create Branch

## Checkout to the upstream branch

```bash
git checkout develop
```

## Pull Latest

```bash
git pull
```

## Create a new branch

```bash
git checkout -b szabolcsthedeveloper/branchName
```

`szabolcsthedeveloper`: the user name of the GitHub, to recognize the user by branch name easily when working with the team

`branchName`: branchName for readability we maintain NamingConvension for naming the branch.


## GIT REBASE

rebase: re-write history commits in a different place

```bash
git rebase <commit-hash>
```

## GIT REVERT

revert: inverse the changes from history and create a new commit 

```bash
git revert <commit-hash>
```

# Deploy and update git repository on a hosted server

These steps assume that the origin of the repository is on a web-based hosting service such as GitHub or BitBucket.

#### **Step 1** Clone a copy of the repository to the server

```bash
ssh yourusername@yourdomain.com
```

Enter you password, and then navigate to the required folder location.

```bash
cd /path/to/folder
```

Clone the repository

```bash
git clone http://bitbucket.com/your-repository
```

**Now that the repository is on the server, lets see how we would update it after making local changes**

#### **Step 2** Update with local repo changes

Let's add a new file to the local repo, commit the changes, and push to origin

```bash
cd ~/my-local/repo
touch new-file.txt
git add .
git commit -m "added new-file.txt"
git push orgin master
```

The new file is now on the BitBucket repo, but not on our web hosting sever. So, we need to ssh back into it, and pull the changes from origin.

```bash
ssh yourusername@yourdomain.com
cd /path/to/repo
```

Now if we run 'git status' you will see that the repo is up to date. This is because we need to ge the latest commit details from origin

```bash
git remote update
```

And pull the changes

```bash
git pull
```


# Single branch for production and development

Consider *master* branch as the single branch for both prod and dev

## Steps to create a branch and merge the branch to master

#### **Step 1** checkout to master and create a branch

```bash
git checkout master

git checkout -b szabolcsthedeveloper/Sample
```

szabolcsthedeveloper/Sample - branch name, choose as you like

> NOTE: Good practice to follow some Naming Convention to create branch names but not mandatory
> szabolcsthedeveloper is the github user name and szabolcsthedeveloper/Sample is the branch name**

#### **Step 2** -  As you are done with some changes to the code, follow

```bash
git status

git add --all

git commit -am "message related to changes done in the branch"

git status

git push -u origin szabolcsthedeveloper/Sample
```

**-a** = all, **m** = message, push all your changes to your remote or origin branch

#### Step 3 - Merge the newly created branch to master

**Step 3.1** - Get the latest from the master, considering that contributors are more than one member

```bash
git checkout master

git pull
```

**Step 3.2** - Merge master to your branch

```bash
git checkout szabolcsthedeveloper/Sample

git merge --no-ff origin master
```

You may get conflicts here if someone modified the same file which you modified

Need to resolve conflicts if any and repeat **Step 2**

**Step 3.3** - Merge your branch to master

```bash
git checkout master

git merge --no-ff origin szabolcsthedeveloper/Sample
```

This completes the flow of basic branching

# GIT MERGE

Merging changes from feature_branch to develop

1. Get latest from develop and merge to feature_branch

```bash
git checkout develop

git pull

git checkout feature_branch

git merge --no-ff origin develop
```

> Note : To be safe from conflict with develop(GOOD PRACTICE), we will resolve in feature_branch

2. Merge feature_branch to develop

```bash
git checkout develop

git merge --no-ff origin feature_branch
```


# GIT RESET

1. Soft Reset

```bash
git reset <commit_hash> --soft
```

2. Mixed Reset

```bash
git reset <commit_hash>

#OR

git reset <commit_hash> --mixed
```

3. Hard Reset

```bash
git reset <commit_hash> --hard
```

# Switching remote URLs from HTTPS to SSH

## List existing URLs

- List your existing remotes to get the name of the remote you want to change.


```code
git remote -v
```

## O/P

```bash
origin	git@github.com:szabolcsthedeveloper/szabolcsthedeveloper.github.io.git (fetch)
origin	git@github.com:szabolcsthedeveloper/szabolcsthedeveloper.github.io.git (push)
```

## Change your remote's URL from SSH to HTTPS

- Change your remote's URL from SSH to HTTPS with the `git remote set-url` command.

```bash
git remote set-url origin https://github.com/USERNAME/REPOSITORY.git
```


