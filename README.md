**hashboot** hashes all files in `/boot` and the MBR to check them during early
boot. It is intended for when you have encrypted the root partition but not the
boot partition. The checksums and a backup of the contents of `/boot` are stored
in `/var/lib/hashboot` by default. If a checksum doesn't match, you have the
option to restore the file from backup.

If there is a core- or libreboot bios and flashrom installed, **hashboot** can check bios for modifications too.

# Install

* Make hashboot executable
* Place hashboot anywhere in $PATH
* Install the appropriate init script
* If applicable, copy kernel-hook to /etc/kernel/post{inst,rm}.d/zzz-hashboot (make sure it is called after all other hooks)
* To generate the manpage, install asciidoc and run `build_manpage.sh`.

# Usage
* First run creates a configuration file. Use bitmask to select desired checkroutines
* Run "hashboot index" to generate checksums and a backup for /boot and MBR
* Run "hashboot check" to check /boot and MBR
* Run "hashboot recover" to replace corrupted files with the backup

# Notes

* You can't use the openrc/sysv init scripts with parallel boot.

# License

```PLAIN
"THE HUG-WARE LICENSE" (Revision 2):
teldra <teldra@rotce.de> and tastytea <tastytea@tastytea.de> wrote this.
As Long as you retain this notice you can do whatever you want with this.
If we meet some day, and you think this is nice, you can give us a hug.
```
