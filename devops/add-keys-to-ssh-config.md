# Add keys to SSH config

To easy make use of git on example BitBucket or github, you can add your private key to the ssh config so it automaticaly used.

Put this in `~/.ssh/config`

```
Host name
 HostName bitbucket.org
 IdentityFile ~/.ssh/deploy-key
```