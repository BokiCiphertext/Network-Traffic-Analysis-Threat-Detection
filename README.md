# Network Traffic Analysis & Threat Detection

## Project overview
: This project demonstrates the transition from offensive security to Defensive Monitoring (SOC Analyst). I executed a stealthy network scan and then used Wireshark to perform forensic analysis, identifying how a defender can "catch" an attacker in real time.

## Tools used 
: * Nmap: For performing the initial reconnaissance scan.
  * Wireshark: For capturing and analyzing the live network traffic.
  * Kali Linux: The primary environment for testing.

## Phase 1: The Attack (Nmap Reconnaissance)
: In this phase I acted as an attacker trying to find open "doors" (ports) on a target server.
  * Command: **nmap -sS -p 1-1000 51.105.71.137**
  * Method: A Stealth SYN scan was used to minimize noise.
  * Result: The scan identified 10 open ports (including HTTP/HTTPS) in 9.78 seconds.

**Figure 1**: Attacker terminal executing the stealth scan on target 51.105.71.137.

## Phase 2: The Detection (SOC Traffic Analysis)
: Switching to the "Detective" role, I used Wireshark to monitor the interface during the attack.
  * Filter Used: **ip.dst == 51.105.71.137**
  * Detection Evidence:
    1. Traffic Flood: Caught a rapid succession of TCP packets hitting port 443.
    2. Network Indicators: Successfully identified [TCP Retransmissions] which serves as a major indicator of scanning traffic.

**Figure 2**: Wireshark dashboard isolating the suspicious traffic flood to the target IP.

## Phase 3: Technical Deep Dive (Packet Details)
: To prove the technical depth of the analysis, I inspected the raw packet data.
  * Evidence: The hex data confirms the specific structure of the TCP packets sent during the reconnaissance phase.

**Figure 3**: Inspecting raw hex data to confirm the "fingerprints" of the Nmap tool.

# Conclusion
: This lab confirms that even "stealth" scans leave significant traces. This "detective" mindset is a critical skill for any SOC Level 1 Analyst focused on threat detection and incident response. 
