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

## Certificates
- add a certificate to your keychain alone with its private key
security import private_key.p12 -k ~/Library/Keychains/login.keychain
security import public_key.pem -k ~/Library/Keychains/login.keychain

[check the certs](1)

## Sync PI
```bash
cd /Users/ricardo/git/thecodestein.com
gulp clean
gulp build
ssh pi@matheus "rm -rf thecodestein/"
ssh pi@matheus "mkdir thecodestein"
scp -r ./dist/* pi@matheus:thecodestein

cd /Users/ricardo/git/thecodestein-backend
sh gradlew installApp
ssh pi@matheus "sudo fuser -k 80/tcp"
ssh pi@matheus "rm -rf thecodestein-backend/"
ssh pi@matheus "mkdir thecodestein-backend/"
scp -r ./build/install/thecodestein-backend/* pi@matheus:thecodestein-backend

ssh pi@matheus "ln -s /home/pi/thecodestein /home/pi/thecodestein-backend/public"
ssh pi@matheus "sudo bash /home/pi/thecodestein-backend/bin/thecodestein-backend --server.port=80 &"



```

[1]: https://www.sslshopper.com/article-most-common-openssl-commands.html