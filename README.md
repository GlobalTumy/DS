Prac 1 : RSA

RSA, named after its creators Rivest, Shamir, and Adleman, is a prevalent public-key cryptosystem pivotal in secure data transmission. It operates with a pair of keys: a public one for 
encryption and a private one for decryption. Its security hinges on the challenge of factoring large prime numbers, making it a stalwart defense. RSA finds extensive application in internet security, safeguarding emails, digital signatures, and HTTPS connections. However, as computing power advances, longer key lengths are advised to uphold its security standards.

install pycryptodome

from Crypto.Publickey import RSA from Crypto import Random
from Crypto.Cipher import PKCS1_v1_5
random generator = Random. new() .read key = RSA.generate(4096, random_generator)message = b'Lokesh KFMSCIT004
cipher = PKCS1_v1_5.new(key)
encrypted message = cipher.encrypt(message)
decrypted message = cipher .decrypt(encrypted message,None)
print("Encrypted message:", encrypted message)
print("Decrypted message:", decrypted_ message)

Prac 2 : IP configuration 

 IP Config Command:
To access network-related details on a Windows system, utilize the "ipconfig" command within the Command Prompt. Upon execution, this command will present a comprehensive overview of network configurations for all interfaces. It encompasses vital information such as IP addresses, subnet masks, default gateways, and additional network interface specifics.

ipconfig/all
This command provides in-depth insights into all network interfaces present on your Windows system. It covers a range of essential details, including IP configuration, MAC address, subnet 
mask, default gateway, DNS servers, and additional relevant information.

ipconfig /displaydns
 This command reveals the contents of the DNS resolver cache within your Windows system. It presents a listing of recently resolved DNS names along with their corresponding IP addresses.

 ipconfig /flushdns
This command serves to flush (clear) the DNS resolver cache, eliminating all entries stored within it. This action prompts the system to re-query DNS servers for subsequent domain resolutions.

wmic os get osarchitecture
This Windows Management Instrumentation Command-line (WMIC) query retrieves information about the operating system architecture (32-bit or 64-bit). When you run this command, it will display either "32-bit" or "64-bit," indicating the architecture of your operating system.


Prac 3 : Browser History Examiner (BHE)

Browser History Examiner (BHE) is a forensic software tool designed to capture, analyze, and generate reports on internet history gleaned from primary desktop web browsers. 
 Its utility extends to a spectrum of digital investigations, including civil and criminal digital 
forensics cases, security incidents, human resources inquiries, and the monitoring of general employee activity.

Step-1: Download and install the BHE from https://www.foxtonforensics.com/browser-history-examiner/download
Step-2: Upon successful installation and initiation of BHE, it will prompt the user to choose between capturing new history data or loading existing history files.
Step-3: The tool will inquire whether you wish to capture historical data from the current computer or from a remote one. Following that, it will prompt you to specify the browser whose history you intend to capture and designate the destination for storing the captured data.
Step-4: It will start capturing the data and will show the captured data so we can analyze it.


Prac 4 : Grabify

Grabify operates as a URL shortening service, akin to platforms like Bitly or TinyURL. However, it has garnered a reputation for its potential involvement in malicious activities. This is due to its capability to 
track and gather information about users who click on the shortened links it generates. Consequently, Grabify has been linked to various privacy and security concerns, as it has been utilized in phishing schemes, online harassment, and other nefarious endeavors. As such, users should exercise vigilance when encountering shortened URLs, particularly those from unfamiliar or dubious sources.

Here's how it typically works:

1) A user creates a shortened URL using Grabify.
2) When someone clicks on the Grabify link, it redirects them to the intended destination.
3) In the background, Grabify logs various information about the visitor, including their IP address, device details, location, and other data.

Step-1: Enter the URL you want Grabify to shorten and track the details.
Step-2: Share the shortened link with another user and when the user opens it, their IP Address and few details will be captured.
Step-3: With the IP address that’s been logged. We can Enter that IP in what is my IP address site and get the location. https://whatismyipaddress.com/


Prac 5 : SMS Bomber
An SMS or phone bomber is a term that refers to a malicious activity where someone sends many unwanted and often repetitive text messages or phone calls to a specific phone number. This is typically done to overwhelm and disrupt the target's communication devices and can be considered a form of harassment.

Step-1: Enter the Phone Number where you want to bomb SMS/phone calls. After adding the number, it will show that the SMS bomb has been started.
Step-2: You can also protect your number, so it won’t be bombed by anyone!


Prac 6 : UI path
UiPath stands as a trailblazer in the realm of Robotic Process Automation (RPA) software, offering 
organizations across diverse sectors a powerful platform to streamline operations and enhance productivity. 
By harnessing the capabilities of software robots to automate repetitive tasks, UiPath empowers human 
workers to redirect their efforts towards tasks that require creativity and problem-solving. This symbiotic 
relationship between automation and human ingenuity heralds a new era of efficiency and innovation in the 
workplace. With UiPath leading the charge, the future of work is characterized by enhanced productivity, 
streamlined processes, and a focus on value-added activities.
Step-1: Access UiPath Studio and initiate the creation of a new process.
Step-2: Incorporate an Input Dialog, SMTP Mail Message, and Message Box into the workflow.
Step-3: provide the port number, server name (smtp.gmail.com), Gmail address, and password. Choose one of the following port numbers for configuration.
For Port, enter one of the following numbers:
For SSL, enter 465.
For TLS, enter 587.
Step-4: Execute the process and input the recipient's email address.
Step 5: - The recipients should receive an email resembling this format.


Prac 7 : Wireshark 
Wireshark is a widely used network protocol analyzer, commonly referred to as a "packet sniffer." It allows users to inspect the data traffic on a computer network in real-time and analyze it for troubleshooting, diagnostic, security, and educational purposes. Wireshark is available for various platforms including Windows, macOS, and Linux. 
Wireshark is widely used by network administrators, security professionals, developers, and educators to analyze and troubleshoot network issues, investigate security incidents, and learn about network protocols and traffic patterns. It's a powerful tool for gaining insights into network communications and diagnosing complex networking problems.

Step-1: Begin by launching Wireshark, where you have the option to either open pre-captured files in formats like pcap or pcapng or initiate a live capture directly from the network.
Step-2: Begin Wireshark in the background and navigate to an insecure website to retrieve the credentials. 
Sample Website: http://testphp.vulnweb.com/login.php
Step-3: Cease capturing data packets, then access the search filter and input "http" to display all packets related to the HTTP protocol.
Step-4: To pinpoint the specific packet, input "http.request.method=="POST"" in the display filter. Once selected, observe that the credentials are revealed within the packet.


Prac 8 : FTK IMAGER 
FTK Imager, developed by AccessData, stands as a pivotal tool in the realm of digital forensics, specifically designed for creating forensic images of various storage devices. Widely utilized in digital investigations, it offers a comprehensive array of features catering to the intricate demands of forensic analysis. With FTK Imager, users can seamlessly perform the following tasks:
Forensic Imaging: Generate precise duplicates of storage devices, including hard drives, USB drives, and memory cards, preserving the integrity of the original data throughout the imaging process.
Mount Forensic Images: Facilitate the analysis of forensic images without modifying the original data, enabling investigators to explore and scrutinize the contents with utmost accuracy.
File Recovery: Uncover and retrieve files residing in unallocated space, providing insights into data that might not be accessible through conventional means.
Hash Calculation: Compute hash values for integrity verification, ensuring the authenticity and integrity of forensic images and collected evidence.
Step-1: Launch FTK Imager Manager and opt for "Create Disk Image."
Step-2: Choose the source as "physical" and designate the physical drive accordingly.
Step-3: Add image destination and select the image type as raw.
Step-4: Provide the details for the evidence item and specify the destination for the image. Name the 
image file as "FTKimg" and adjust the Image Fragment Size to 0.
Step-5: It will start creating the image file and then you can verify the results.
Step-6: Go to the given destination and verify the result.


Prac 9 : nCAT
Ncat stands as a robust networking utility within the Nmap suite, renowned for its prowess in network 

exploration, security auditing, and network service administration. This command-line tool facilitates the 
seamless exchange of data across network connections, bolstered by support for a diverse range of 

protocols including TCP, UDP, SSL, and IPv6.Ncat is a versatile networking utility for:
1. Port scanning and service discovery.
2. Network troubleshooting and traffic inspection.
3. Secure remote administration.
4. File transfer, with support for encryption.
Note: 
NCAT is a Cli based tool
Reverse shell : session created using remote/attacker system
Bind shell : session created using target system


Prac 10 : SQL injection 
SQL injection attacks occur when attackers input malicious SQL statements into input fields or parameters of a web application. These injections can bypass authentication, retrieve sensitive data, modify database contents, or even execute administrative operations on the database server. The vulnerability arises from improper sanitization or validation of user inputs in the application code, allowing attackers to manipulate 
SQL queries. To mitigate SQL injection risks, developers should use parameterized queries, input validation, and proper access controls to prevent unauthorized database access. Regular security audits and updates are essential to identify and patch potential vulnerabilities, safeguarding against such attacks
Step1: Launch SQLMap on Kali Linux.
Step 2: Input the command for SQLMap to inject the payload and retrieve the database from the vulnerable website.
Step 3: Now we’ve access of DB lets get into the table using SQL map
Step 4: Delve deeper into what information this table contains.
Step 5: We notice that tables have columns such as "name" that we can access. This hack demonstrates 
that even without logging in or escalating privileges, data can be accessed through SQL injection.


Prac 11 : Maltego 
Maltego serves as a tool for data visualization and analysis, utilized primarily for information gathering and intelligence purposes. It empowers users to collect and scrutinize data from diverse sources such as public databases, social networks, and online services, enabling the creation of 
visual representations that highlight relationships and connections between various entities.
In contrast, SQL injection stands as a cyber attack method targeting web applications reliant on SQL (Structured Query Language) databases. This attack exploits vulnerabilities within these applications, wherein the attacker inserts malicious SQL code into input fields or parameters. By 
doing so, the attacker manipulates the application into executing unintended SQL commands. The ramifications include unauthorized access to sensitive data, data manipulation, and potential complete takeover of the database server.While Maltego itself is not expressly designed for executing SQL injection attacks, it can be employed during the reconnaissance phase of an attack. In this capacity, it aids in gathering 
information about potential targets and identifying vulnerabilities that could be exploited via SQL injection techniques.

Step1: Register and go to the home page.
Step 2: In the toolbar above, choose "Machines," then select "URL to Network and Domain 
Information." This option enables the search for all potential connections associated with the provided 
URL.
Step 3: Enter the URL you want to Investigate.
Output: Every connection to Hinduja College website is visible in connective manner


Prac 12 : PuttySSH
PuTTY is a free and open-source terminal emulator, serial console and network file transfer application. It supports several network protocols, including SCP, SSH, Telnet, rlogin, and raw socket connection. It can also connect to a serial port. The name "PuTTY" has no official meaning. PuTTY was originally written for Microsoft Windows, but it has been ported to various other operating systems. Official ports are available for some Unix-like platforms, with work-in-progress ports to Classic Mac OS and macOS, and unofficial ports have been contributed to platforms such as Symbian, Windows Mobile and 
Windows Phone. PuTTY was written and is maintained primarily by Simon Tatham, a British programmer.
Prerequisite:
1. Apt update: To download all the updates.
2. apt install openssh-server: to install ssh services.
3. Install putty to the client OS (i.e., Host OS windows) 
4. apt install ufw
Step 1: Check the SSH status
Step 2: Service ssh start to start the ssh service.
Step 3:
UFW stands for Uncomplicated Firewall. It's a program that manages firewall rules in Linux. 
UFW is designed to be easy to use and has a command-line interface. It's available by default in all Ubuntu installations since 8.04 LTS.
UFW uses iptables to configure firewall rules. Iptables has a complex syntax, so using UFW is a useful 
alternative. UFW minimizes the effort of setting up a firewall by starting with an optimal default configuration. 
UFW can be used in: Arch Linux, Debian, Ubuntu. UFW can use either iptables or nftables as the back-end firewall.
UFW can be used to: 
Allow by specific port, IP address, and protocol
Allow IP address 192.168.0.4 access to port 22 using TCP
Step 4: Now we’ve given all the persmission lets make the file which we will transfer via ssh.
Step 5: Copy the kali IP and paste it in PUTTY.
Step 6: Accept it.
Step 7: Login by entering credential(mostly for ssh [kali, kali] is [login, pass]
Step 8: Escalate the user from normal user to root user.
Step 9: Finally got into the directory where is saved the file.
Step 10: Same File can be access from kali VM into the Host OS via SSH.
Step 11: we’ve edited the kali’s file from host OS and it is reflected into the KALI VM also.
