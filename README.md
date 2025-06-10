This is preconfigured to my system. Nonetheless, perform following commands:

Check your battery with cat:

1. cat /sys/class/power_supply/BAT(1 or 0)/charge_control_end_threshold

Knowing whether you have BAT1 or BAT0 is important or else the threshold won't work.

Make a systemd service at the /etc/systemd/system/. Name the service so that it is easy to identify.

2. sudo vim /etc/systemd/system/charge-control-end-threshold.service

Change the permissions of the file:

5. sudo chmod 644 /etc/systemd/system/charge-control-end-threshold.service

Reload systemctl:

6. sudo systemctl daemon-reload

Enable and start the service

7. sudo systemctl enable charge-control-end-threshold.service
8. sudo systemctl start charge-control-end-threshold.service

Reboot and check if the service is working:

9. reboot
10. cat /sys/class/power_supply/BAT(1 or 0)/charge_control_end_threshold

After catting to the file, it should return with the value you desire:

80
