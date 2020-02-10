# Git Setup

## Installation and configuration

Install git client and configure global identity values

```bash
~> sudo apt install git
~> git config --global user.name "user_name"
~> git config --global user.email "email_address"
```

## Setup ssh keys

Check if ssh is already configured.  
Generate new ssh keys using ed25519 encryption which is now better than rsa.

```bash
~> ls -al ~/.ssh     # This should error as there is no ssh configuration yet
~> ssh-keygen -t ed25519 -C "comments here"
  - <enter>
  - <password>
```

Start ssh agent and add the new key to the authentication agent

```bash
~> eval $(ssh-agent -s)
~> ssh-add ~/.ssh/id_ed25519
  - <password>
```

You might need to install keychain to memorize the password.

```bash
~> sudo apt-get install keychain
~> eval `keychain --eval id_ed25519`
```

## Use a repo

Add the content of your id_ed25519.pub to [github](https://github.com/settings/keys).  
Clone your repository.

```bash
~> cat ~/.ssh/id_ed25519.pub       # Copy result to github
~> git clone git@<your_repository>.git
```
