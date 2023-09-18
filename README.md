# Find Credentials in FTP and Perform Gobuster

We will start by enumerating the target. Our first step is always through nmap scan.

![2](https://github.com/ggouw/FTP-and-Gobuster/assets/120260071/1e009a87-39bc-44a5-a20a-65638b991a86)

From here we can see two open ports: 21 and 80.\
Port 21 is dedicated to FTP (File Transfer Protocol), meaning that it's primary use is to transfer files between hosts on the same network.\
Also we can see this FTP server is configured to allow anonymous login:\
![3](https://github.com/ggouw/FTP-and-Gobuster/assets/120260071/1cf1c1c0-9a03-45fc-8e76-04f850cc0548)

Next step, we are going to connect to the remote FTP server, and we can fill 'anonymous' for username.\
Server does not request a password, by inputting the 'anonymous' username. it's sufficient for us to receive 230 Login successful.

![4](https://github.com/ggouw/FTP-and-Gobuster/assets/120260071/d896030a-2e1a-4349-a1f4-b9a494771181)

Available commands.\
![5](https://github.com/ggouw/FTP-and-Gobuster/assets/120260071/f82b78a3-7016-4a38-a7ca-79c342ab3e28)

We will use 'dir' to list the directories and 'get' to download.

![6](https://github.com/ggouw/FTP-and-Gobuster/assets/120260071/c668b83f-541e-4a55-a962-d008ba0ad427)

![7](https://github.com/ggouw/FTP-and-Gobuster/assets/120260071/0b0a60cb-ae41-4c65-be28-3eec0962877b)\
![8](https://github.com/ggouw/FTP-and-Gobuster/assets/120260071/12aa437c-8416-41e1-84ab-2501b2d95faa)\
![9](https://github.com/ggouw/FTP-and-Gobuster/assets/120260071/a02fdf56-13ee-4571-82fc-fd3842eeaaaa)

After exit we can check with 'ls' command to see if our files are downloaded.

![10](https://github.com/ggouw/FTP-and-Gobuster/assets/120260071/e18f33ce-5cd9-4488-86aa-e7d5e8cbd864)

We can use the 'cat' command, to open the files.

![11](https://github.com/ggouw/FTP-and-Gobuster/assets/120260071/f0859b12-7160-45ae-9241-2fa83f31fc87)

Once we obtained the credentials, the next step is to check if they are used on the FTP service for access.
FTP server returns code '530 This FTP server is anonymous only'.

![12](https://github.com/ggouw/FTP-and-Gobuster/assets/120260071/6031a3d8-ac30-4eab-a251-3b420c1b4c78)

We have one option left. During the nmap scan, the service running on port 80 was reported as.\
![13](https://github.com/ggouw/FTP-and-Gobuster/assets/120260071/cc31e746-dff5-412a-a2ad-45506dd96c39)

We can typing the IP address of the target into our browser URL search bar.

![14](https://github.com/ggouw/FTP-and-Gobuster/assets/120260071/c0a2d84c-fb78-423a-961f-8ff3fc511d0d)

Now we need to use gobuster as our tool to navigating any hidden or hardly accessible directories and pages.

<li> dir : Uses directory/file enumeration mode.</li>
<li> --url : The target URL.</li>
<li> --wordlist : Path to the wordlist.</li>
<li> -x : File extension(s) to search for.

![1](https://github.com/ggouw/FTP-and-Gobuster/assets/120260071/491b5ca0-e30c-43c0-8679-dad4a1673c01)

From here, we found one interesting files which is,\
![15](https://github.com/ggouw/FTP-and-Gobuster/assets/120260071/50fa4c09-8913-4815-bf88-5c300bbb797a)

If we navigate this to our browser URL, we will present with a login page asking for a username & password.

![16](https://github.com/ggouw/FTP-and-Gobuster/assets/120260071/2005ebfb-3ab9-4c16-8411-a0eee37973c5)

For this, we can attemp to login using the previous credentials.

![17](https://github.com/ggouw/FTP-and-Gobuster/assets/120260071/95156929-9419-40f2-b0fd-dfe85e08ff57)

And now we manage login as admin to the server and got the flag as well.

![18](https://github.com/ggouw/FTP-and-Gobuster/assets/120260071/fb037e67-a7c1-4c3e-8a34-b0a8296e6647)



























