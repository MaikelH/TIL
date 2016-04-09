# Add iptable rule on line number

For connecting to SSH it easier and safer to use a keypair than passwords. To 
create a public/private keypair use the following command.

First get the line numbers 

```
iptables -nL --line-numbers
```

Now we can use the line number to insert the rule at the specified line.

```
iptables -I INPUT {LINE_NUMBER} -p tcp --dport 21 -j ACCEPT
```