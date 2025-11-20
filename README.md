# Windows-Firewall
Firewall Rules


Objective: Configure and test basic firewall rules to allow or block traffic.


1. Open Firewall Configuration Tool

Windows:
  Open "Windows Defender Firewall with Advanced Security" via Control Panel or search.  
  Or use PowerShell for commands.

  Linux (UFW): 
  Open terminal to use UFW commands.

2. List Current Firewall Rules

Windows PowerShell: 
  ```powershell
  Get-NetFirewallRule | Format-Table -Property Name, Enabled, Direction, Action
  ```

  Linux (UFW):
  ```bash
  sudo ufw status numbered
  ```

3. Add Rule to Block Inbound Traffic on Port 23 (Telnet)

Windows PowerShell:
  ```powershell
  New-NetFirewallRule -DisplayName "Block Telnet Port 23" -Direction Inbound -LocalPort 23 -Protocol TCP -Action Block
  ```

Linux (UFW):
  ```bash
  sudo ufw deny 23/tcp
  ```

4. Test the Rule

- Attempt to connect to port 23 on your machine using telnet locally or from another machine:  
  ```bash
  telnet <your_machine_ip> 23
  ```
  The connection should fail due to the block.

5. Add Rule to Allow SSH (Port 22) (Linux)

Linux (UFW):
  ```bash
  sudo ufw allow 22/tcp
  ```

Windows: SSH is usually not applicable on standard Windows unless configured specifically.

6. Remove the Test Block Rule to Restore Original State

Windows PowerShell:
  ```powershell
  Remove-NetFirewallRule -DisplayName "Block Telnet Port 23"
  ```

  Linux (UFW):  
  ```bash
  sudo ufw delete deny 23/tcp
  ```
7. Document Commands or GUI Steps Used

- Save the commands used in a text file or screenshot the Windows Firewall GUI showing the rules.

8. Summary: How Firewall Filters Traffic

- Firewalls filter network traffic by applying rules that allow or block connections based on criteria such as port number, protocol, IP address, and direction (inbound or outbound). This helps protect systems from unauthorized access and potential attacks by controlling which network packets are permitted.
