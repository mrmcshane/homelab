# Neofetch

Neofetch is a tool that gives pretty server stats when you log on.

## Install

Get the neofetch repo:
```
curl -o /etc/yum.repos.d/konimex-neofetch-epel-7.repo https://copr.fedorainfracloud.org/coprs/konimex/neofetch/repo/epel-7/konimex-neofetch-epel-7.repo
```

Install neofetch:
```
yum install -y neofetch
```

Remove the neofetch repo:
```
rm /etc/yum.repos.d/konimex-neofetch-epel-7.repo
```

Create the neofetch config at `/root/.config/neofetch/config.conf`:
```
print_info() {
    prin ""
    info "OS" distro
    info "Host" model
    info "Kernel" kernel
    info "Uptime" uptime

    prin ""
    info "Local IP" local_ip
    info "Public IP" public_ip

    prin ""
    info "CPU" cpu
    info "Memory" memory
    info "Disk" disk
    prin "Disk (/data)" "$(df -h | grep /data | tr -s ' ' | cut -d ' ' -f3) / $(df -h | grep /data | tr -s ' ' | cut -d ' ' -f2) ($(df -h | grep /data | tr -s ' ' | cut -d ' ' -f5))"

    prin ""
    prin "State" "$(mdadm -D /dev/md5 | egrep -i 'State :' | cut -d: -f2)"
    prin "Active" "$(mdadm -D /dev/md5 | egrep -i 'Active Devices :' | cut -d: -f2)"
    prin "Working" "$(mdadm -D /dev/md5 | egrep -i 'Working Devices :' | cut -d: -f2)"
    prin "Failed" "$(mdadm -D /dev/md5 | egrep -i 'Failed Devices :' | cut -d: -f2)"
    prin "Spare" "$(mdadm -D /dev/md5 | egrep -i 'Spare Devices :' | cut -d: -f2)"
}
```


Add a bash profile script to call neofetch in a clean way by creating `/etc/profile.d/neofetch_profile.sh`:
```
#!/usr/bin/env bash

alias neo='neofetch --config /root/.config/neofetch/config.conf --ascii_colors 5'
neo
```