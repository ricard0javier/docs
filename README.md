# Shared Documentation

This is a common place where I can put information that I sould like to share or that I think will forget any tyme soon

## System information commands
Raspbian: 
```bash
cat /etc/os-release
```

## Git and SSH
- generate your public/private key pair set:

```bash
mkdir ~/.ssh
cd ~/.ssh
ssh-keygen
```

- Next you need to copy this to your clipboard.

```bash
cat id_rsa.pub | pbcopy
```

- Add your key to your account via the website.

- Finally setup your ~/.gitconfig

```bash
git config --global user.name "ricard0javier"
git config --global user.email villanueva.ricardo@gmail.com
```
