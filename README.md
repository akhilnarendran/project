

SCAN YOUR LOCAL NETWORK FOR OPEN PORTS


 TASK DAY1

WHAT WE NEED 

• A computer running Windows, macOS, or Linux

• Administrator/root privileges on your machine

• Connection to a local network (home/office Wi-Fi or Ethernet)






Step 1: Install Nmap
1. Download Nmap:
• Visit the official Nmap website: https://nmap.org/download.html

• Download the appropriate version for your operating system



• Install Nmap:


• <img   width="225" height="225" alt="Image" src="https://github.com/user-attachments/assets/58233213-9f6e-47dd-8459-1dcb185b96a9"/>
• 



◇ Windows: Run the installer and follow the prompts (include Npcap when asked)
 <img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/5c9e98af-cdca-4c06-94e0-623b1acd11a3" />

◇ macOS: You can use Homebrew (brew install nmap) or download the macOS installer
           
    brew install nmap          
           
◇ Linux: Use your package manager (e.g., sudo apt install nmap on Ubuntu)

    apt update && upgrade   -y
    sudo apt install nmap  -y 


Step 2: Find Your Local IP Range
1. Find your IP address:

• Windows: Open Command Prompt and type ipconfig

• macOS/Linux: Open Terminal and type ifconfig or ip a


<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/6eb22832-580d-4be2-92ab-69a7e81d4497" />



• Identify your network range:
◇ Look for your IPv4 address (typically starts with 192.168.x.x or 10.x.x.x)

◇ The subnet is usually /24, meaning the first three numbers are fixed (e.g., 192.168.1.0/24)


# my Local Network Details

    - Interface used: wlan0
    - Local IP: 10.142.147.113/24
    - Network Range Scanned: 10.142.147.0/24


Step 3: Perform the Scan

1. Basic scan command:

        more about nmap tool  we can use this  command   nmap --help  or nmap -h  or  man nmap   this result  show all   about nmap  usage  
							sudo  nmap -sS 192.168.1.0/24


        				 nmap -sS 192.168.1.0/24
		      	(Replace 192.168.1.0 with your network range)


                 Alternative scan options:
       ⇒ For a more detailed scan: nmap -sS -A 192.168.1.0/24
         For a faster scan: nmap -sS -T4 192.168.1.0/24
       ⇒ To save results to a file: nmap -sS -oN scan_results.txt 192.168.1.0/24



Step 4: Analyze Results
 
 this  was  the  result     
 (sudo nmap   -sS   10.142.147.113/24 -oN find_ips.txt     in my  case )   
 
 <img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/f1dff3c5-cbb1-4f4e-94a7-077e1fb30da9" />

we can see  one ip    is this  10.142.147.74   ok why we can  use more   power  add in scan   i use   this  option   (-A )

    sudo nmap -sS -A  10.142.147.113/24 -oN  For-a-more-detailed-scan.txt 
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/e696b262-079b-4865-b8e7-3d64577ca6e1" />

i can find some more informations about  ip   
 
    PORT   STATE            SERVICE                       VERSION
    53/tcp    open                 domain                      dnsmasq 2.51
    | dns-nsid: 
    |_  bind.version: dnsmasq-2.51
    MAC Address: 06:D3:5D:1B:CD:8C (Unknown)
    Device type: phone
                  
                      'its a phone '
                      
• The device is running dnsmasq 2.51 on port 53
• dnsmasq is a lightweight DNS forwarder commonly found on mobile devices and IoT equipment
• Version 2.51 is somewhat outdated (current version is 2.90+)


                                       
    Common ports to note: 22 (SSH), 80 (HTTP), 443 (HTTPS), 21 (FTP), 3389 (RDP) 
    
    22 – SSH (Secure Shell) → Remote terminal access
    80 – HTTP → Unsecured web traffic
    443 – HTTPS → Secure web traffic
    21 – FTP (File Transfer Protocol) → File transfers
    3389 – RDP (Remote Desktop Protocol) → Windows remote desktop


    this  are Common ports ,  but  in my case  no  hope  for this  

next  i   specifically  scan the ip 10.142.147.74   use this  tool   and  zenmap  and  wireshark  

<img width="225" height="225" alt="Image" src="https://github.com/user-attachments/assets/b395087c-1a5d-40b4-8ace-d112f48bea79" />

<img width="225" height="225" alt="Image" src="https://github.com/user-attachments/assets/c537e3d9-3ef7-41d5-b579-f5dfc6b392d0"/>


nmap scan report <img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/5908818a-8f8d-49af-9fd9-988ab18414b3" />


almost same as the perverse   but i use different tools to scan this ip again    

<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/23f519a9-54b8-4050-a619-fa41eaed36d4" />







Optional Wireshark Analysis
1. Install Wireshark (if you want to see the network traffic):
• Download from https://www.wireshark.org/

• Install with default options





<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/0b75f7bd-8d7f-4d13-85d7-4589f2f73cf6" />



<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/881d3e71-5879-420c-9288-561ca23cf12a" />





 
 
 
 i  find  what i need  and  how to  test  it the  port  and device  
 
 
 we can see  the poet  dns ans  tcp  traffic  on this 10.142.147.74 ip   and what  the communication on going this  src ip (source IP) and dis ip (destination ip) 


 

                      
