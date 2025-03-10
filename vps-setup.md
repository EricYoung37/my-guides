# Things to Do When Getting a New VPS

1. Update and upgrade

```
apt update
apt upgrade
```

2. Change SSH Port in `/etc/ssh/sshd_config`

   Remeber to `$ systemctl restart ssh`

3. Create a non-root user

   - `$ adduser <new-user-name>`
   - install `sudo` by `$ apt update && apt install sudo`
   - give `sudo` privilege by `$ visudo`
   - add `${new-user-name} ALL=(ALL:ALL) ALL` under `User Privilege Specification`

4. Stop remote SSH access for the root user in `/etc/ssh/sshd_config`

   - **Ensure new user can login** before proceed
   - Change `PermitRootLogin Yes` to `PermitRootLogin No`.
   - Remeber to `$ systemctl restart ssh`

5. Create an RSA key pair for SSH login and stop password login
   - generate `EdDSA/Ed25519` keys
   - save public key in <new-user-name>'s root directory in `.ssh/authorized_keys`
   - `$ chmod 600 ~/.ssh/authorized_keys` (RW by owner)
   - In `/etc/ssh/sshd_config`, set `PubkeyAuthentication Yes` and `PasswordAuthentication No`
   - `$ sudo systemctl restart ssh`
   - Add private key to PuTTY
   - **Don't close the current terminal** before ensuring the keys work.

6. Edit `.gitconfig`
```
$ git config --global user.name <your-name>
$ git config --global user.email <your-email>

$git config --global gpg.format ssh
$git config --global user.signingkey ~/.ssh/<example-key>.pub
$git config --global commit.gpgsign true

$ git config --global -l | grep user
```
