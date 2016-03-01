# Change default Grub entry

Check available entries
```
$ sudo grep menuentry /boot/grub2/grub.cfg
if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
  menuentry_id_option=""
export menuentry_id_option
menuentry 'Fedora (4.4.2-301.fc23.x86_64) 23 (Server Edition)' --class fedora --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-4.4.2-301.fc23.x86_64-advanced-4b95cddc-7d77-4c77-b793-2b75f365c108' {
menuentry 'Fedora (4.3.3-300.fc23.x86_64) 23 (Server Edition)' --class fedora --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-4.3.3-300.fc23.x86_64-advanced-4b95cddc-7d77-4c77-b793-2b75f365c108' {
menuentry 'Fedora (4.2.8-300.fc23.x86_64) 23 (Server Edition)' --class fedora --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-4.2.8-300.fc23.x86_64-advanced-4b95cddc-7d77-4c77-b793-2b75f365c108' {
menuentry 'Fedora (0-rescue-91cc317c76244bc6bc46ff7bfe45e8da) 23 (Server Edition)' --class fedora --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-0-rescue-91cc317c76244bc6bc46ff7bfe45e8da-advanced-4b95cddc-7d77-4c77-b793-2b75f365c108' {
```

Adjust the desired default entry through the `GRUB_DEFAULT` key into `/etc/default/grub`. e.g.
```
GRUB_DEFAULT='Fedora (4.3.3-300.fc23.x86_64) 23 (Server Edition)'
```

Remake grub configuration (for UEFI systems)
```
sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg
```
