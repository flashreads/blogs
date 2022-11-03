id	title	tags	 	author	meta-description	date	keywords	template	categories	cover
015-wget-howto.md	assign ip address usage short guide	linux	ip address	chandresh1339	how to assign ip address in linux	10/28/2021 12:30	linux,ip address,debian,ubuntu	post	linux	../../images/categories/linux.png

How to Set Static IP Address in Debian / Ubuntu.

IP address: 192.168.0.100
Netmask: 255.255.255.0
Hostname: node01.tecmint.com
Domain name: tecmint.com
Gateway: 192.168.0.1
DNS Server 1: 8.8.8.8
DNS Server 2: 4.4.4.4
To setup static IP address in Debian/ Ubuntu, open the following file:
# nano /etc/network/interfaces
You may see a line looking like this:
auto eth0
iface eth0 inet dhcp
Change it so it looks like this:
auto eth0
iface eth0 inet static 
  address 192.168.0.100
  netmask 255.255.255.0
  gateway 192.168.0.1
  dns-nameservers 4.4.4.4
  dns-nameservers 8.8.8.8
Save the file and then edit /etc/resolv.conf like this:
# nano /etc/resolv.conf
nameserver 8.8.8.8 # Replace with your nameserver ip
nameserver 4.4.4.4 # Replace with your nameserver ip
Restart the networking on your system with:
# /etc/init.d/network restart  [On SysVinit]
# systemctl restart network    [On SystemD]
Your static IP address has been configured.

