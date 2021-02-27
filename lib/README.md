# Lib

Most of the Plan 9 programs default to \$HOME/lib/\* when searching for configuration files. This repo contains plumbing rules, my [Rc](http://doc.cat-v.org/plan_9/4th_edition/papers/rc) profile, [nyne](https://git.sr.ht/~danieljamespost/nyne) configuration, and other useful files.

# Mounting Acme with 9p

`mkdir -p $HOME/n/acme`
`9mount -i 'unix!/tmp/ns.'$USER'.:0/acme' $HOME/n/acme`

`mount -t 9p /tmp/ns.daniel.:0/acme n/acme -o trans=unix,uname=daniel`

# Dependencies

## Go
- 9fans.net/go/acme/editinacme
- github.com/mpl/xplor

## Other
- https://www.stunnel.org/
- http://sqweek.net/code/9mount/
