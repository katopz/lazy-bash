# lazy-bash
Lazy bash belong here

#### Output to file

- `>` or `1>` Redirects `stdout` to file.
- `2>` Redirects `stderr` to file.
- `&>` Redirects `stdout` and `stderr` to file.
- `/dev/null` is a blackhole.

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
### Fix Host key verification failed.
> To fix `WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!`

```shell
ssh-keygen -R YOUR_HOST_IP_OR_DOMAIN
```
