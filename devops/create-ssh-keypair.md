# Create SSH keypair

For connecting to SSH it easier and safer to use a keypair than passwords. To 
create a public/private keypair use the following command.

```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```