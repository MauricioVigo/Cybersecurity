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

- **2-** we know Both of our machines are in the same network but we dont know the ip of the M87 so one easy way to find out is with <code>nmap</code> we are going to use
the ***-sn*** argument that will perform a ping scan use for network discovery 
![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/53191213-46d6-4552-a391-2399683bd003)

- **3-** now we know the IP for M87 is 

