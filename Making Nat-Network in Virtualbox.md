# Connection 

I'm going to show you how to set up your virtual machines on the same network so they can communicate with each other.

I'll be using right now Virtualbox 7.0

<code>Virtualbox 7.0</code>

We will have one Kali machine serving as the attacker and one DVWA machine known for its vulnerabilities. 

The Kali machine will have access to the internet and to DVWA, while the DVWA machine will only have a connection to the Kali machine.

- **1-** First, we have to create a Nat-Network. Click on ***Tools*** and choose the ***Nat Networks*** tab.
![1](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/dcf2acda-790d-4a4e-9c70-9d94bfc55e6f)


- **2-** Click ***Create***, and your new network will appear with a default name, in the ***General Options*** at the bottom, you can rename it according to your preference.
In my setup, I've named it Nat Network and assigned a 10.0.1.0/24 IP. Once you've made your choices, click ***Apply*** to finalize, and your new Nat Network will be complete.
![2](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/aa11643b-aaad-49d7-a0a1-85ef7989d6d0)


- **3-** Afterward, navigate to your initial VM, mine is the DVWA, and proceed to click on ***Settings***.
![3](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/0e943ff6-22ef-4c7e-8613-a2740da89104)


- **4-** Next, access the ***Network*** tab and modify the ***Attached to*** option to ***Nat-Network***, select the name you assigned to the network in the previous step in my case,
Nat Network, subsequently, navigate to the ***Advanced*** settings and, under ***Promiscuous Mode***, set it to ***Allow All***, enabling this mode allows the VM to intercept and capture all network traffic, and it might be usefull. Once adjustments are complete, click ***OK*** to confirm.
![4](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/12b927f7-44e5-432d-9f33-60cd3f99a8d7)


- **5-** Now that your initial VM is configured, proceed to the Kali VM. Access the ***Settings*** menu and navigate to ***Network***, you'll notice that ***Adapter 1*** is set to ***Nat***,
a configuration crucial for internet access, leave this setting unchanged. Now, move to the ***Adapter 2*** tab, enabling the network adapter by clicking ***Enable Network Adapter***.
![5](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/1f9cfbad-4197-473d-8063-ccb21e7ece5d)


- **6-** Next, replicate the steps performed on the previous VM, under ***Attached to***, select ***Nat Network*** and choose the name of the network we were using, set ***Promiscuous
  Mode*** to ***Allow All***, confirm the changes by clicking ***OK***. By completing these steps on both machines, you have successfully configured them for use.
![6](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/6a50739f-1629-4b1b-b57f-59c065e15106)


- **7-** Access the terminals on both machines and execute ***ifconfig***, observe that Kali has the IP address 10.0.1.4, while DVWA is assigned 10.0.1.5. To confirm connectivity
initiate a ***ping*** from each machine to the IP address of the other. Successful replies from both indicate established connectivity
![7](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/1b6fb176-5023-480c-8642-c46a707718fe)


- **8-** For the final step, open the browser on Kali and enter the IP address of DVWA to test accessibility, successful access confirms the established
connectivity between both machines.
![8](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/8d3f2ede-ddb1-496c-b6a4-baccdf9fd3fa)
