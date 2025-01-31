# Capturing Packets with tcpdump

## Project Description


In this project, I used tcpdump to capture live network traffic on a Linux virtual machine as part of my daily tasks for a hypothetical company. I identified network interfaces, used tcpdump to filter and capture network traffic, and saved the data in a packet capture (p-cap) file. Finally, I examined the captured packet data to focus on specific types of traffic, enhancing my skills in network traffic analysis and packet inspection. This hands-on experience enhanced my ability to monitor and investigate network traffic using tcpdump.

### Skills Learned


- Proficiency in using tcpdump to capture and analyze live network traffic
- Ability to inspect and interpret detailed packet information, such as TOS, TTL, protocol types, and TCP flags
- Ability to identify the different available network interfaces


## Tasks

### Task 1: Identifying Network Interfaces
My first task was identifying which network interfaces I could use to capture network packet data. I used the command <b>ifconfig</b> to list which networks I could use for this task. Its output is pictured in the screenshot below. 

![image](https://github.com/user-attachments/assets/bd591bdb-0881-432c-84c6-eba8c9223f32)

The first option I noted was the Ethernet network interface,<b>eth0</b>. The other one listed, <b>lo</b> (or <b> loopback interface</b>), is a virtual interface mostly used for troubleshooting issues. I wanted to capture network packets and, therefore, decided to use tcpdump on the Ethernet network interface. I ran the command <b>sudo tcpdump -D</b> to verify that this was possible. 

![image](https://github.com/user-attachments/assets/e3e431bb-d724-4d71-84a6-bc880d23a9b3)

The interface <b>eth0</b> was listed as up and running in the output, meaning I could use tcpdump on the network without issue.

### Task 2: Inspecting a Network Interface
My next task was to inspect a few packets from live <b>eth0</b> network traffic using tcpdump. More specifically, I wanted to view extensive packet data, including TOS, TTL, offset, flash, and internal protocol types. To properly view this data, I ran a tcpdump command with a few options. The option <b>-i</b> allowed tcpdump to capture data specifically from a network, which in this case was the <b>eth0</b> interface. The <b>-v</b> option displayed detailed packet information. Lastly, the <b>-c5</b> option specified how many packets I wanted to see ( five in this case). The command and its output are displayed below. 

![image](https://github.com/user-attachments/assets/d70e4d0f-d2aa-4cfd-98c6-dbb309676a34)


#### Exploring Packet Details
Below is a quick breakdown of the first packet:

1. The first line of the packet output reported on the interface that tcpdump was listening on (<b>eth0</b>) and provided information on the link type and capture size
   ![image](https://github.com/user-attachments/assets/5323016b-7643-48f5-85d4-4e9a0cfef8b7)
2. On the next line was the packet's timestamp and protocol type
   
   ![image](https://github.com/user-attachments/assets/18be0aa0-fe45-4b07-b60f-a005b8323f1c)
4. It also listed information about IP packet fields, such as TOS, TTL, and other detailed information I requested using the <b>-v</b> verbose option.
    ![image](https://github.com/user-attachments/assets/d1c7dcd3-e6f4-4e9a-a99b-039b3188a55f)
5. The next section showed the systems that communicated with each other. tcpdump converted the IP addresses into names, which included the port number as a suffix.
   ![image](https://github.com/user-attachments/assets/3e364d6a-ce00-44c0-9865-c6fa7cf22578)
6. The remaining part of the packet specified its TCP packet header data. This included TCP flags (P for pushing out data), checksum value ( for detecting errors), and packet length.
   ![image](https://github.com/user-attachments/assets/a5e9418f-b3c8-4f61-a1ea-46647477ff38)

### Task 3: Capturing Network Traffic

For this task, I needed to save captured network data to a capture file. This time, I wanted to save a small sample of HTTP(TCP Port 80) traffic only. I used the following command to capture packet data into a file named <b>capture.pcap</b>:
![image](https://github.com/user-attachments/assets/55a7174d-91cb-4fcb-a593-dbc04ba577fc)

This command ran tcpdump in the background with the following options:
- <b>-i eth0</b>: captured data from the Ethernet interface.
- <b>-nn</b>: prevented tcpdump from resolving IP addresses to ports/names. This is the most secure practice, as omitting it may alert malicious actors during investigations.
- <b>-c9</b>: captured nine packets of data before stopping.
- <b>port 80</b>: filtered only for port 80 traffic (HTTP default port)
- <b>-w capture.pcap</b>: saved the data to a named file
- <b>&</b>: instructed the shell to run this command in the background. 
  

Then, I ran the command <b>curl opensource.google.com </b> to generate some HTTP traffic. I noticed the <b>301 Moved</b>. No further investigation was needed.

![image](https://github.com/user-attachments/assets/63dbe703-ba87-46ff-995a-7cd97a50c118)

To verify that the packet data was captured, I ran the following code:

![image](https://github.com/user-attachments/assets/2de52681-873d-4d3b-be01-73a6c1d6e545)

The traffic data was successfully saved in <b>capture.pcap</b> as specified in the initial tcpcdump command.


### Task 4: Filtering Captured Packet Data
My final task was to filter data from the saved packet capture file, <b>capture.pcap</b>. I used the following command and got its output:
![image](https://github.com/user-attachments/assets/370de4da-3c44-4264-996d-0627e837798c)

Here is a list of the options I used for this command:
- <b>-nn</b>: ensured that port/protocol name lookup was disabled
- <b>-r capture.pcap</b>: read captured data from the specified file
- <b>-v</b>: verbose; displayed detailed packet data.
  
Lastly, I wanted to view extended packet information, such as the hexadecimal and ASCII outputs of the packet data. This information is important during investigations as any suspicious patterns or anomalies could warn an analyst of potential malware. 
  
![image](https://github.com/user-attachments/assets/d5922bd9-e24e-4657-a131-da0290291372)

I used the <b>-X</b> option here to enable tcpdump to display the hexadecimal and ASCII information associated with the packet. 


## Summary 
In this project, I demonstrated how to use tcpdump to capture and analyze network traffic from a Linux virtual machine. I began by identifying available network interfaces and choosing the Ethernet interface (eth0) for packet capture. I then inspected live traffic, focusing on detailed packet data including TOS, TTL, and protocol types. After capturing a sample of HTTP traffic and saving it to a file, I verified the capture and filtered the data for analysis. This project provided practical experience in network traffic analysis and using tcpdump for security investigations.

