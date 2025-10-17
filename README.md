# Python aiohttp package for Termux (Android)

## Purpose

Version made as a workaround for the `Could not contact DNS servers` error.\
~~Makes streamrip work on Android.~~\
This will fix streamrip on Android, but it's better to instead just uninstall `aiodns` as per nathom/streamrip#894:
```bash
source /data/data/com.termux/files/home/.local/share/pipx/venvs/streamrip/bin/activate
python -m pip uninstall aiodns
deactivate
```

## Usage example with custom DNS servers

```bash
DNS_SERVERS=1.1.1.1,1.0.0.1 your-command
```

## Installation on Termux

```bash
mkdir aiohttp-termux-dns-fix
cd aiohttp-termux-dns-fix
pip download aiohttp==3.13.0
tar -xzf aiohttp-3.13.0.tar.gz
cd aiohttp-3.13.0
curl -L https://github.com/OothecaPickle/aiohttp/commit/08fd9cc9b01800c4f982f1dfc89e35989962698e.patch -o fix.patch
patch -p1 < fix.patch
pipx inject -f streamrip .
cd ../..
rm -rf aiohttp-termux-dns-fix
```
