## Guide for SSH Connection between PC and GitHub

**Note:** Commands are running in **Git for Windows**.

### Generating a new SSH key and adding it to the ssh-agent [🔗](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent?platform=linux)

Later we'll configure Git and the ssh-agent so we don't need to start the agent and add keys every time we start a new terminal.

We can use the command below to check if the ssh-agent is running with any keys added to it.

```
$ ssh-add -L
```

### Adding a new SSH key to your GitHub account [🔗](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account?platform=linux)

### Auto-launching ssh-agent on Git for Windows [🔗](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/working-with-ssh-key-passphrases#auto-launching-ssh-agent-on-git-for-windows)

Note `ssh-add` defaults to `~/.ssh/id_rsa`. We may need to change it to the path where we generated our own key.

Alternatively, I personally prefer the below method to automatically add SSH keys.

### Persisting SSH keys in the ssh-agent [🔗](https://stackoverflow.com/a/64866985)

The `.ssh/config` file allows us to store different SSH options for each remote machine we connect to.

With `IdentityFile`, the SSH agent doesn't need to try and add all keys. Even if `ssh-add -L` will output `The agent has no identities.`, the SSH connection will succeed.
