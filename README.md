# Enables miscellaneous debug settings #

Ships a /etc/default/grub.d/30_output_verbose.cfg configuration file, that
removes `quiet` from the `GRUB_CMDLINE_LINUX_DEFAULT` variable and adds
`debug=vc` to the kernel boot parameter to enable verbose output during the
initial ramdisk boot phase.

Undo debugging related sysctl settings by package security-misc.

Enables persistent systemd journal log.

Disables /lib/systemd/coredump.conf.d/disable-coredumps.conf by package
security-misc by creating a symlink from
/etc/systemd/coredump.conf.d/disable-coredumps.conf to /dev/null.
debian/debug-misc.links

Disables panic-on-oops, remove-system.map by security-misc.

Coredumps are enabled.
/etc/security/limits.d/40_debug-misc.conf

Coredumps may contain important information such as encryption keys or
passwords. Package security-misc disables doredumps. Package debug-misc
re-enables coredumps.

For better usability, to ease debugging in case of issues.

For better security, this package should only be installed on specific
machines that require debugging. Unfortunately, security and debugging are
conflicting optimization goals.
## How to install `debug-misc` using apt-get ##

1\. Download [Whonix's Signing Key]().

```
wget https://www.whonix.org/patrick.asc
```

Users can [check Whonix Signing Key](https://www.whonix.org/wiki/Whonix_Signing_Key) for better security.

2\. Add Whonix's signing key.

```
sudo apt-key --keyring /etc/apt/trusted.gpg.d/whonix.gpg add ~/patrick.asc
```

3\. Add Whonix's APT repository.

```
echo "deb https://deb.whonix.org buster main contrib non-free" | sudo tee /etc/apt/sources.list.d/whonix.list
```

4\. Update your package lists.

```
sudo apt-get update
```

5\. Install `debug-misc`.

```
sudo apt-get install debug-misc
```

## How to Build deb Package from Source Code ##

Can be build using standard Debian package build tools such as:

```
dpkg-buildpackage -b
```

See [instructions](https://www.whonix.org/wiki/Dev/Build_Documentation/debug-misc). (Replace `package-name` with the actual name of this package.)

## Contact ##

* [Free Forum Support](https://forums.whonix.org)
* [Professional Support](https://www.whonix.org/wiki/Professional_Support)

## Donate ##

`debug-misc` requires [donations](https://www.whonix.org/wiki/Donate) to stay alive!
