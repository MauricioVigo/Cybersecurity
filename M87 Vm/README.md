# M87 Writeups
I'll explain how to access a VM designed for penetration testing called M87. You can download the VM here <code>[M87](https://www.vulnhub.com/entry/m87-1,595/)</code>

>[!NOTE]
>We need to set up both machines on the same network so that they can communicate with each other, if you're unsure how to do this, you can follow the steps below.

- <code>[Virtualbox](https://github.com/MauricioVigo/Cybersecurity/blob/main/Making%20Nat-Network%20in%20Virtualbox.md)</code>

- <code>[Vmware](https://github.com/MauricioVigo/Cybersecurity/blob/main/Making%20Nat-Network%20in%20Vmware.md)</code>

<br>

<a name="index"></a>
# Table of contents
1. [First Steps](#step1)
2. [Nmap Network Discovery](#step2)
3. [Nmap Port-Service Scan ](#step3)
4. [Login Interfaces](#step4)
5. [Crawling with Wfuzz](#step5)
6. [Hidden login](#step6)
7. [Injectable Hidden parameter](#step7)
8. [Sql Injection with Sqlmap](#step8)
9. [Getting users and passwords with Sqlmap](#step9)
10. [Reading /etc/passwd with Sqlmap](#step10)
11. [Getting access to the victims terminal](#step11)
12. [Reverse shell](#step12)



We are going to use a Kali linux as the attacker and the M87 as the victim

Let's begin!"

<a name="step1"></a>
## Step 1
When launching M87, we notice a login prompt, but we lack both the username and password.

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/f2688039-a89b-486b-bc38-cd590b1b5c93)

<br> 

<a name="step2"></a>
## Step 2
We are aware that both of our machines exist within the same network. However, the IP address of M87 remains unknown. To resolve this, we can employ the <code>nmap</code> tool with the -sn argument, which conducts a ping scan for network discovery.

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/c66154ff-2561-4d62-b0f6-06e132cc77c0)

<br> 

[Back](#index)
<a name="step3"></a>
## Step 3
Now that we have identified the IP for M87 as 192.168.1.9, we will proceed with a port scan using <code>nmap</code> to determine the version and type of service running on each port. Our scan reveals two open ports, 80 and 9090. Let's explore further.

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/274db07e-87aa-4df3-b8a4-df3980a2f898)

<br> 

[Back](#index)
<a name="step4"></a>
## Step 4
On both ports, we observe the presence of two login interfaces.

<code> Port 80 </code>

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/4049d0ae-4ba8-4d6d-a29b-1ecb2f0edde9)

<code> Port 9090 </code>

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/5aea1dd4-6bee-4149-9a59-fccb4993e640)

<br>

[Back](#index)
<a name="step5"></a>
## Step 5
We will attempt to perform crawling using <code>wfuzz</code> to identify any hidden content. Upon examination of both ports, we discover valuable information exclusively on port 80, we uncover two assets: ***assets*** and ***admin***.

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/38e48ccb-442e-4569-801d-7cf0f0f881ca)

<br>

[Back](#index)
<a name="step6"></a>
## Step 6
Of the two of them only admin proves to be valuable, upon investigation, we encounter another login interface, this particular login includes a hidden parameter, ***id***, it is important to highlight that the existence of concealed parameters are often essential for the database query, and may not be visible but can be recall as in this case with the 'ID' parameter."
![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/f7e27bf3-51f7-410a-9096-3e73b5b062b0)

<br>

[Back](#index)
<a name="step7"></a>
## Step 7
We experiment with different values including the ID, into the logging system, and it responds with a name, so its a confirmation that the value is indeed injectable.

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/40e555d6-6ac5-4417-a2fc-e8652fe8d3eb)

<br>

[Back](#index)
<a name="step8"></a>
## Step 8
We want to find out the name of the database. To do this, we use a tool called <code>sqlmap</code>. We run a command with the tool, providing the IP address and the vulnerable parameter ID to execute the injection and get the database name.

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/cd581992-cabf-480e-8ae0-8be7fbce388a)
![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/c836c3cc-6ef2-47c5-b269-d9c98a2098ed)

<br>

[Back](#index)
<a name="step9"></a>
## Step 9
Now that we know what the database is called, we're going to gather all the information it has inside.
![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/5a221b90-9093-4516-83d8-ff625888dea6)
![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/d81754c0-14b0-4489-bb6c-9230812e88b7)

<br>

[Back](#index)
<a name="step10"></a>
## Step 10
As we can see, the passwords are in plain text, so there's no need to crack them, even though we tried different usernames and passwords for the logins without success, it seems like we might be missing something. To investigate further, we're trying to get the passwd file to see which users the server has.

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/0b0ff6b2-14eb-48b4-9473-9ae11e0c85d0)

We're going to the folder where the saved file is and checking what's inside.
![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/1109112f-9e5f-4dd8-b8ab-7dcdc8feb1c8)

<br>

[Back](#index)
<a name="step11"></a>
## Step 11
After checking the passwd file, we found that besides ***root*** the only other user is ***charlotte***, now that we have the username, we'll use the admin password we discovered in the database.

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/5d4619dc-9772-4836-b067-f0b5343b5e66)

<br>

[Back](#index)
<a name="step12"></a>
## Step 12
The user and password were correct allowing us to gain access. We then move into the terminal granting us nearly complete control over the PC.

As an additional step if we rather not use their website terminal, we can easily set up a reverse shell using netcat.

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/6d39976f-6751-4daf-bc21-c3e30f8ab38f)


We run the ***nc*** command in our kali machine with the options ***-lnvp*** like in the image below where: 
 - ***-l*** tells netcat that it should operate in listening mode.
 - ***-n*** tells that the ip will be in numbers to skip DNS resolution.
 - ***-v*** means verbose that will provide more detailed information about the process.
 - ***-p*** allows us to specify the port number that is going to use.

In the victims terminal in port 9090 we run this command: 

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/74814dcd-d0d6-49d5-98c6-e6e75197a5e7)

- ***-e*** instructs netcat to execute the next command, which in this case is /bin/bash, at the specified target IP address and port.

After everything is ready we got back to our kali terminal and we can see that we have direct access to the victims pc

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/1fda81eb-7402-4b2a-9617-c02ffb573d4f)

[Back](#index)


