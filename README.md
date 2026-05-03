# slackpkg-update-notify
Shows a popup if new Slackware patches or updates found  

## Installation

## Binary
Follow indroduction on [release](https://github.com/rizitis/slackpkg-update-notify/releases)

## Build

1.  `git clone   https://github.com/rizitis/slackpkg-update-notify.git`
2.  `cd slackpkg-update-notify/SlackBuild || exit 1 `
3.  `su -c "bash slackpkg-update-notify.SlackBuild"`
4.  `su -c "upgradepkg --install-new --reinstall /tmp/slackpkg-update-notify-0.2-noarch-1_custom.txz"`

###    After installation finish as root:
> paste these lines in /etc/rc.d/rc.local
```
# Slackpkg update notify
if [ -x /usr/bin/slk-changelog-check ]; then
logger -t rc.local "starting slk-changelog-check"
echo "starting slk-changelog-check" 
sleep 120 && /usr/bin/slk-changelog-check &
fi
```




You cat watch behavor from `/var/log/messages` something like this: `cat /var/log/messages | grep slk`

```
May  2 16:56:24 hackbox rc.local: starting slk-changelog-check
May  2 16:58:24 hackbox slk-changelog-check: Fetched 3 lines from ChangeLog.
May  2 16:58:24 hackbox slk-changelog-check: No changes detected.

```
