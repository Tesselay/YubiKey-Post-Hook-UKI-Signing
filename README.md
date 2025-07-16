# YubiKey Post Hook UKI Signing

This is a small **mkinitcpio** post hook that will trigger a signing process to the UKI provided using any inserted YubiKey and `systemd-sbsign`.

It will check if a YubiKey is inserted, if the provided slot has any private key in it and whether the UKI is already signed by the YubiKey, skipping the process if the result is not correct.

Will ask for a PIN when the slot is configured as such.

## Features

- Works with multiple YubiKeys (Will only sign with one)

## Installation

Clone repository and move/cp the file to `/etc/initcpio/post/`. Make it executable.

```bash
$ mv uki-sign-yk /etc/initcpio/post/uki-sign-yk
$ chmod +x /etc/initcpio/post/uki-sign-yk
```

**Remember to set the correct db slot inside the script!**

## Usage

It will auto execute on every UKI generation when using mkinitcpio.

Test it by invocating the script directly or by rebuilding the UKI.

```bash
$ /path/to/uki-sign-yk /path/to/UKI.efi
```

```bash
$ mkinitcpio -P
```
