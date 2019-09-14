# How to install NextCloud on Raspberry Pi

1. Install Raspbian
2. Put **ssh** empty file at root
3. connect with pi/raspberry
4. connect to wifi with
	network={
	  ssid=""
	  psk=""
	  }
  5. Install nextcloud https://linuxconfig.org/how-to-install-nextcloud-on-debian-10-buster-linux
  6. Format USB Drive in **ext4**
  7. Plug it 
  8. https://raspberrytips.com/mount-usb-drive-raspberry-pi/
	  - `sudo fdisk -l`
	  - Find path /dev/xxx
	  -   `sudo ls -l /dev/disk/by-uuid/`
	  - Find the UUID
	  -  `sudo nano /etc/fstab`
	  - `UUID=********  /path/to/mount ext4  defaults   0       0`
	   - `sudo mount -a` or just reboot
  9. Edit the *www/var/html/nextcloud/config/config.php*
  10. Change **datadirectory** path by the one of your USB drive 
  11. `sudo chown www-data:www-data -R path/of/usb`
  12. `sudo /etc/init.d/apache2 restart`
  13. `cd /var/www/html/nextcloud/`
	  - `sudo -u www-data php occ maintenance:mode --off`
	  - It will disable maintenance mode in case it was activated and check if all the access are ok
  14. Check on the UI if everything is ok 
  15. Download the mobile APP and remember to be in the same network as the Rasp
