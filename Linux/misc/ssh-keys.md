# SSH Keys

To create or add SSH keys on Linux, MacOS & Windows. Windows users without OpenSSH can install and use PuTTY instead.

## To create a new key pair, open a terminal:

`ssh-keygen`

Enter a name and location for the key.

`Generating public/private rsa key pair. Enter file in which to save the key (/Users/USER/.ssh/id_rsa):`

Create and confirm a passphrase for the key:

```
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
```

Two files will be produced called id_rsa and id_rsa.pub. Next, add this public key.

## Add the public key

Copy and paste the contents of the .pub file, typically id_rsa.pub, into the SSH key content field on the left.

`cat ~/.ssh/id_rsa.pub`
