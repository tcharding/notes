Systemd Notes 
=============

__see https://wiki.archlinux.org/index.php/Systemd__

Basic commands
 # systemctl
 # systemctl status
 # systemctl list-units
 # systemctl --failed
 # systemctl list-unit-files

 # systemctl start _unit_
 # systemctl stop _unit_
 # systemctl restart _unit_
 # systemctl reload _unit_
 # systemctl status _unit_
 # systemctl is-enabled _unit_
 # systemctl enable --now _unit_
 # systemctl help _unit_

System Startup/Poweroff

 # systemctl reboot
 # systemctl poweroff
 # systemctl suspend
 # systemctl hibernate
 # systemctl hybrid-sleep

Get current target
 $ systemctl list-units --tpye=target

Change current target

 # systemctl isolate rescue.target <!-- activate runlevel 1  -->





