# GitHub


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
