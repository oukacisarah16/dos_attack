# dos_attack
Sure, here is a step-by-step guide on how to perform a SYN flood attack and port scan using `hping3`, including setting up the virtual machines and monitoring the target's network performance.

---

### Step-by-Step Guide to Performing a SYN Flood Attack and Port Scan

#### Step 1: Set Up Virtual Machines
1. **Open Oracle VM VirtualBox**.
2. **Create and configure two virtual machines**:
   - **Kali Linux**:
     - Download the Kali Linux ISO from the official website.
     - Create a new virtual machine and choose the downloaded Kali Linux ISO as the installation media.
     - Follow the installation steps to set up Kali Linux.
   - **Windows XP**:
     - Obtain a Windows XP ISO or installation disc.
     - Create a new virtual machine and choose the Windows XP ISO or disc as the installation media.
     - Follow the installation steps to set up Windows XP.
3. **Ensure both virtual machines are connected to the same network** (e.g., using NAT Network or Host-Only Adapter in VirtualBox settings).

#### Step 2: Start the Virtual Machines
1. **Launch both the Kali Linux and Windows XP virtual machines** from Oracle VM VirtualBox.
2. **Log in** to both machines with appropriate user credentials.

#### Step 3: Install `hping3` on Kali Linux
1. **Open a terminal** in Kali Linux.
2. **Install `hping3`** using the following command (if not already installed):
   ```sh
   sudo apt-get update
   sudo apt-get install hping3
   ```

#### Step 4: Perform a Port Scan on the Target Machine
1. **Determine the IP address** of the Windows XP machine (e.g., `192.168.56.103`).
2. **Run the port scan** from the Kali Linux terminal:
   ```sh
   hping3 --scan 1-65535 192.168.56.103 -S --rand-source
   ```
   - This scans all ports (1-65535) on the target IP address using TCP SYN packets with random source IP addresses.
3. **Note the open ports** from the scan results.

#### Step 5: Perform a SYN Flood Attack
1. **Choose an open port** to target from the previous scan (e.g., port 135).
2. **Run the SYN flood attack** from the Kali Linux terminal:
   ```sh
   hping3 -S 192.168.56.102 -a 192.168.56.103 -p 135 --flood
   ```
   - This sends a flood of TCP SYN packets to port 135 of the target IP (192.168.56.103), with the source IP spoofed as 192.168.56.102.
3. **Monitor the attack output** in the terminal.

#### Step 6: Monitor Network Performance on the Target Machine
1. **Open Performance Monitor** on the Windows XP machine:
   - Go to **Start > Programs > Administrative Tools > Performance**.
2. **Set up a network monitoring graph**:
   - In the Performance window, right-click on the graph area and choose **Add Counters**.
   - Select **Network Interface** from the list of counters and choose the appropriate network adapter.
   - Click **Add** and then **OK** to start monitoring network performance.
3. **Observe the network utilization graph** for any spikes or unusual activity.

#### Step 7: Analyze Results and Conclude
1. **Review the network performance data** on the Windows XP machine to determine the impact of the SYN flood attack.
2. **Conclude the experiment** by stopping the `hping3` attack on the Kali Linux machine using `Ctrl + C`.
3. **Document the findings**:
   - Note the open ports discovered during the scan.
   - Describe the impact observed on the network performance of the target machine.
   - Suggest potential mitigation strategies to prevent such attacks in real-world scenarios.

### Conclusion
This guide provides detailed steps to perform a SYN flood attack and port scan using `hping3` from Kali Linux, and to monitor the impact on a target Windows XP machine. By following these steps, one can understand the process of network reconnaissance and attack, as well as the importance of network security measures.

---
