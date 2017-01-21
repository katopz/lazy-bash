# lazy-bash
Lazy bash belong here

#### Add SSH to server
```shell
# Config
export SERVER=root@foo.bar
export SSH_PUBKEY=~/.ssh/id_rsa.pub

# Add
ssh $SERVER sh -c "'cat >> .ssh/authorized_keys'" < $SSH_PUBKEY

# Verify
ssh $SERVER cat .ssh/authorized_keys

```
