# GitHub


## Git commands
[Git](https://git-scm.com/docs)

### Initialize/Clone projects

| Commands   | Info
|:-----------|:-----
|```git clone <url>``` | Clone a repository
|```git init``` | Initialize an empty git repository [```--initial-branch=<branch-name>``` - set the name for the branch]


### Basic Snapshotting


| Commands   | Info
|:-----------|:-----
|```git add <files/folders>``` | Stage selected file changes
|```git add <.>``` | Stage all changed files
|```git rm <files/folders>``` | Remove files from the staged area
|```git status``` | Show the diffrences from the current HEAD commit
|```git commit -m <"commit_msg">``` | Commit staged changes


### Branching and Merging


| Commands   | Info
|:-----------|:-----
|```git branch``` | List existing git branches
|```git branch -a``` | List branches remote and local branches
|```git branch <branch_name>``` | Create a new branch
|```git branch -d``` | Delete a branch [```-D``` - delete force]
|```git checkout``` | Change HEAD to the current branch
|```git checkout <branch_name>``` | Switch and set the HEAD to the branch
|```git checkout -b <branch_name>``` | Create and switch to a new branch
|```git merge <branch_name>``` | Merge <branch_name> into current branch

```
                                git merge branch1
     C--D       branch1                                      C--D       branch1
    /                                                       /    \
A--B--E         *main                                   A--B--E---F     *main
```


### [Git graph](https://en.wikipedia.org/wiki/Git#Data_structures)
```
------------|           |---------------------------------------------------|
| Remote    |           | Local                                             |
|-----------|           |---------------------------------------------------|
|           |           | Clone     | Branches      | Working Files         |
|           |           |-----------|---------------|-----------------------|
|           |           |           |               |                       |
|      ------------pull-------------------------------->                    |
|           |           |           |               |                       |
|           |           |           |       -------checkout-------->        |
|           |           |           |               |                       |
|           |           |-----------|               |                       |
|           |           |                           |                       |
|           |           |                           |                       |
|           |           |                           |-----------|           |
|           |           |                           | Stage     |           |
|           |           |                           |           |           |
|       <------push----------               <---commit---  <----add----     |
|           |           |                           |           |           |
|-----------|           |---------------------------------------------------|
```

## Authentication
### SSH Key
#### [Generate a new SSH Key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key)
- Create key with the command:
    - Ed25519 Algorithm
  ```
  ssh-keygen -t ed25519 -C "{your_email_address}"
  ```
    - RSA Algorithm (legacy system that doesn't support Ed25519)
    ```
    ssh-keygen -t rsa -b 4096 -C "{your_email_address}"
    ```



### [Add the SSH Key to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent)
- Start the ssh-agent in the background
```
eval "$(ssh-agent -s)"
```
- Add your SSH **private** key to the ssh-agent
```
ssh-add ~/.ssh/{key_name}
```
- Add the SSH public key to GitHub

### [Add the SSH public Key to GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account#adding-a-new-ssh-key-to-your-account)
1. Go to ```Settings```
1. Go to ```SSH and GPG keys```
1. Click ```New SSH key``` or ```Add SSH key```
1. Add the **public** ssh key

### [Test the ssh connection](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection)
```
ssh -T git@github.com
```

Result:
```
Hi {your_name}! You've successfully authenticated, but GitHub does not provide shell access.
```


### Personal access token (PAT)
- Create a PAT (Treat PATs like a password)
    - fine-grained personal access token (recommended by GitHub)
    - personal access token (classic)

- [Create a fine-grained (PAT)](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-fine-grained-personal-access-token)

1. Verify your email address
1. Go to ```Settings```
1. Go to ```Developer settings```
1. Click on ```Personal access token``` > ```Fine-grained tokens```
1. Generate new token
1. Select ```Permissions```


- Clone a GitHub repository with a PAT
```
git clone https://{USER}:{PAT}@github.com/{REPOSITORY}
```
