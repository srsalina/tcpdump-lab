# Capturing Packets with tcpdump

## Objective


The Detection Lab project aimed to establish a controlled environment for simulating and detecting cyber attacks. The primary focus was to ingest and analyze logs within a Security Information and Event Management (SIEM) system, generating test telemetry to mimic real-world attack scenarios. This hands-on experience was designed to deepen understanding of network security, attack patterns, and defensive strategies.

### Skills Learned


- Advanced understanding of SIEM concepts and practical application.
- Proficiency in analyzing and interpreting network logs.
- Ability to generate and recognize attack signatures and patterns.
- Enhanced knowledge of network protocols and security vulnerabilities.
- Development of critical thinking and problem-solving skills in cybersecurity.


## Steps

### Identifying Network Interfaces
My first task was identifying which network interfaces I could use to capture network packet data. I used the command <b>ifconfig</b> to list which networks I could use for this task. Its output is pictured in the screenshot below. 

![image](https://github.com/user-attachments/assets/bd591bdb-0881-432c-84c6-eba8c9223f32)

The first option I noted was the Ethernet network interface,<b>eth0</b>. The other one listed, <b>lo</b> (or <b> loopback interface</b>), is a virtual interface mostly used for troubleshooting issues. I wanted to capture network packets and, therefore, decided to use tcpdump on the Ethernet network interface. I ran the command <b>sudo tcpdump</b> to verify that this was possible. 

![image](https://github.com/user-attachments/assets/7f619116-6321-46c9-b8d9-4a1fe919bbb5)

### Inspecting a Network Interface
Next, 
TOS, TTL, offset, flash, and internal protocol type. 

To properly view this data, I needed to run a tcpdump command with a few options. The option <b>-i</b> allowed tcpdump to capture data specifically from a network, which in this case was the <b>eth0</b> interface. 

The command and its output are displayed below. 
![image](https://github.com/user-attachments/assets/d70e4d0f-d2aa-4cfd-98c6-dbb309676a34)


### Exploring Network Packet Details


## Capturing Network Traffic

For the next task, I needed .

![image](https://github.com/user-attachments/assets/5caee54b-8d4c-43fa-8ce5-ebe258ca02d7)
![image](https://github.com/user-attachments/assets/e8090d6f-0642-4d29-b5be-df3fba64fb87)
![image](https://github.com/user-attachments/assets/30852226-3925-4604-8bc1-95437c847d68)



