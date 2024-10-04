# Step 1: Install VirtualBox
Follow the steps mentioned in the assignment
# Step 2: Create and Configure the VM
Open the Virtual Box give every details as mentioned in the page but instead of giving ISO use the downloaded file as a hard disk
Attach the .vdi File as a Hard Disk:
Select Add Hard Disk button (‘+’ icon)
In the dialog box, choose the option to Select Existing Disk.
Navigate to your downloaded Ubuntu .vdi file and select it.

# Step 3: Host a Website on Nginx
Change to the default Nginx web directory
cd /var/www/html
Replace the existing index.html file
$ sudo mv index.nginx-debian.html index.html
$ sudo nano index.html
<html>
<head>
    <title>Welcome to awesomeweb in ubuntu</title>
</head>
<body>
    <h1>Welcome to awesomeweb in ubuntu!</h1>
</body>
</html>

Check the website: http://<VM-IP>
To fetch VM IP run the command "ip a" or 'ifconfig' or 'hostname -i'

Look for the IP address under your network interface, typically something like 192.168.x.x or 10.0.x.x.

# Step 6: Scan the VM from Your Host Machine Using Nmap
Install Nmap on host machine:
sudo apt install nmap
nmap <VM-IP>

# Result
ralph@LAPTOP-4R7IUU73:/mnt/c/Users/johni$ nmap -Pn 127.0.0.1
Starting Nmap 7.93 ( https://nmap.org ) at 2024-10-04 23:26 IST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000019s latency).
All 1000 scanned ports on localhost (127.0.0.1) are in ignored states.
Not shown: 1000 closed tcp ports (conn-refused)

Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds
