# Mail in Acme

- Install msmtp

```
brew install msmtp
```

- Move this repo to \$home/mail and create outgoing file

```
mv ./mail $home/mail
touch $home/mail/outgoing
```

- Create secrets

```
mkdir $home/mail/secrets
echo mypassword > $home/mail/secrets/myaccountpass.gpg
gpg --full-generate-key
gpg -r email.address@domain.com -e $home/mail/secrets/myaccountpass.gpg
```

- Make sure these are running

```
plumber
factotum
```

- Authenticate to factotum server

```
factotum -g 'proto=pass service=imap server=imap.gmail.com user=daniel@martin.ai !password?'
mailfs -t imap.gmail.com
```

- Configure msmtp with something like the following

```
logfile $home/.cache/msmtp.log

defaults
auth on
port 587
tls on

account work
host smtp.gmail.com
port 587
from daniel@martin.ai
user daniel@martin.ai
passwordeval "gpg --quiet --for-your-eyes-only --no-tty --decrypt $home/mail/secrets/myaccountpass.gpg"
```
