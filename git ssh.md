# Reference

https://help.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

# Adding your SSH key to the ssh-agent

Start the ssh-agent in the background.

`eval "$(ssh-agent -s)"`

modify your ~/.ssh/config file to automatically load keys into the ssh-agent and store passphrases in your keychain.

```
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
```

Add your SSH private key to the ssh-agent and store your passphrase in the keychain.

`ssh-add -K ~/.ssh/id_rsa`
