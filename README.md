# lazy-bash
Lazy bash belong here

#### Add SSH to server
```shell
export SERVER=root@foo.bar
export SSH_PUBKEY=~/.ssh/id_rsa.pub
ssh $SERVER << EOF
cat "" >> ~/.ssh/authorized_keys
cat $SSH_PUBKEY >> ~/.ssh/authorized_keys
EOF
```
