# lazy-bash
Lazy bash belong here

### Create `cert.key` and `cert.pem`
```shell
# Create cert.key and cert.pem for a certificate that is valid for the next 10 years.
sudo openssl req -x509 -sha256 -newkey rsa:2048 -keyout cert.key -out cert.pem -days 1024 -nodes -subj '/CN=www.foo.com'
```
### Output to file

- `>` or `1>` Redirects `stdout` to file.
- `2>` Redirects `stderr` to file.
- `&>` Redirects `stdout` and `stderr` to file.
- `/dev/null` is a blackhole.

### Add SSH to server
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
