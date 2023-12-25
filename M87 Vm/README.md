# M87 Writeups
Im going to explain how to get access to a VM made for pentesting called M87, you can download the VM here <code>[M87](https://www.vulnhub.com/entry/m87-1,595/)</code>

>[!NOTE]
>we have to set up both machines in the same Network so they can comunicate with each other, if you dont know how to do it you can find they steps down here. 

- <code>[Virtualbox](https://github.com/MauricioVigo/Cybersecurity/blob/main/Making%20Nat-Network%20in%20Virtualbox.md)</code>

- <code>[Vmware](https://github.com/MauricioVigo/Cybersecurity/blob/main/Making%20Nat-Network%20in%20Vmware.md)</code>

We are going to use a Kali linux as the attacker and the M87 as the victim

Now we are going to start!!

- **1-** when we launch the M87 we see they have a Login but we have no idea about the password or user name and we need to find out.

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/f2688039-a89b-486b-bc38-cd590b1b5c93)

<br> 

- **2-** we know Both of our machines are in the same network but we dont know the ip of the M87 so one easy way to find out is with <code>nmap</code> we are going to use the ***-sn*** argument that will perform a ping scan use for network discovery

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/c66154ff-2561-4d62-b0f6-06e132cc77c0)

<br> 

- **3-** now that we know the IP for M87 that is 192.168.1.9 we will do a port scan with <code>nmap</code> to see witch version and type of service is running on each port, we see 2 ports open 80 and 9090, so lets go take a look.

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/274db07e-87aa-4df3-b8a4-df3980a2f898)

<br> 

- **4-** on both ports we see there are 2 loggings 

<code> Port 80 </code>

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/4049d0ae-4ba8-4d6d-a29b-1ecb2f0edde9)

<code> Port 9090 </code>

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/5aea1dd4-6bee-4149-9a59-fccb4993e640)

<br>

- **5-** We are going to try to do some crawling with <code>wfuzz</code> and check if there are any hidden content, after check with both ports we only find something usefull in port 80, and we find 2 assets and admin.

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/38e48ccb-442e-4569-801d-7cf0f0f881ca)

<br>

- **6-** 



