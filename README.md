# lazy-bash
Lazy bash belong here

## TODO
- [ ] http://www.tldp.org/LDP/abs/html/index.html
- [ ] https://github.com/Idnan/bash-guide

## Random topics

### Kill process by port number
> Kill firebase-tools that use 4400,5000,5001,8080
```shell
kill -9 $(lsof -it:4400,5000,5001,8080)
```

### Multiple line .env
```shell
DO_OPTION=$(cat <<EOF
'{
  "name": "My-Droplet",
  "region": "nyc2",
  "size": "512mb",
  "image": "ubuntu-14-04-x64"
}'
EOF)
```

### To see macOS power consumtion
```shell
system_profiler SPPowerDataType
```
### Read .env
```shell
# Create some .env
echo "FOO=123" > .env

# Use it
source .env; echo $FOO
```

### Creating a self-signed ssl cert
```shell
# Create cert.key and cert.pem for a certificate that is valid for the next 10 years.
openssl req -x509 -newkey rsa:4086 \
-keyout key.pem -out cert.pem \
-days 3650 -nodes -sha256
```
### Output to file
- `>` or `1>` Redirects `stdout` to file.
- `2>` Redirects `stderr` to file.
- `&>` Redirects `stdout` and `stderr` to file.
- `/dev/null` is a blackhole.
- `echo $'export NVM_DIR="$HOME/.nvm"\n. "/usr/local/opt/nvm/nvm.sh"' >> ~/.bash_profile`

### Apply from source
```shell
source ~/.bash_profile
```

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
## Replacement
### Repace $FOO with BAR
```shell
src='Hello $FOO'
match='$FOO'
repl='BAR'
echo ${src/$match/$repl}
# Hello BAR
```

### Replace template file with `ENV`
```shell
# Create template
echo "Hello {{FOO}}" > foo.conf.tmpl

# Replace {{FOO}} with FOO variable and output to new foo.conf file 
sed -e "s|{{FOO}}|$FOO|g" foo.conf.tmpl > foo.conf

# Multiple replacement
sed -e "s|{{FOO}}|$FOO|g;s|{{BAR}}|$BAR|g" foo.conf.tmpl > foo.conf
```
