# Connection 

I'm going to show you how to set up your virtual machines on the same network so they can communicate with each other.

I'll be using right now VMware Workstation Pro 17

<code>Vmware Workstation pro 17</code>

We will have one Kali machine serving as the attacker and one DVWA machine known for its vulnerabilities. 

The Kali machine will have access to the internet and to DVWA, while the DVWA machine will only have a connection to the Kali machine.

## Step 1
We have to make a virtual network where all our devices will communicate with each other, To do this, navigate to ***edit*** and then ***Virtual Network Editor***

![1](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/f95d0cbb-c326-4ebf-8477-7ab6b70c9b49)

<br>

## Step 2
When you open the editor, you'll find all the default connections already present. Simply click on ***add Network***

![2](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/2e18d8bb-edf2-4aa0-8baf-154bc7543567)

<br>

## Step 3
Select any of the default names and click ***OK***

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/a9b67bfa-41a1-43fd-bb27-ab83eb5b4656)

<br>

## Step 4
You can rename the network to make it easier to find. In this case, I will name it ***Nat-Network***, make sure that the ***Host-Only*** option is selected 

![3](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/48f1cfc9-a31d-474e-8e00-8b9108275b28)

<br>

## Step 5
Now, change the Subnet IP and mask to your preferred values. In my case, I'm using 192.168.1.0/24, for the DHCP option, you can specify the range or lease times, im only changing the starting IP address so the firts host will start with x.x.x.1 

![4](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/e42ef964-1af7-48c8-9b17-38faa39e431d)

<br>

## Step 6
Return to the main menu, select the first VM, and click on ***Edit Virtual Machine Settings***, In my case, I am using the DVWA VM, which will have only one network adapter because an internet connection is not necessary

![5](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/76fdf027-241c-47df-8cc4-75ef9820869d)

<br>

## Step 7
In the ***Hardware*** Tab click on ***Network Adapter*** and change the ***Network Connection*** to ***Custom*** and select the name of the ***Virtual Network*** we created

![6](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/d6203a45-e2b2-4d41-be72-231ec7e2b424)

<br>

## Step 8
As we want to give this VM access to the internet, we need to add one more network adapter. The existing one allows the VM to connect to the internet. To do this, go to VM options, navigate to the ***hardware tab*** click on ***Add...*** and choose ***Network Adapter*** then click ***Finish***, this will create a ***Network Adapter 2*** that we need to configure for our custom Nat-Network, just like we did in the example with DVWA.

![7](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/1c325c17-de2e-4c74-95d4-561a5b90a321)

<br>

## Step 9
after its done the Kali will look like this

![8](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/59718fa7-17ba-45c8-a37b-bdf389421ddf)

<br>

## Step 10
Now its time to check if both of the Vms can comunicate with each other, open both of them and execute ifconfig to see the IP of each one, the ***192.168.1.105 for the DVWA*** and the ***192.168.1.1 for the Kali***, perform a ping on both of them to see if you get a reply. As we can see, they both have communication.

![9](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/7a51e9bd-32f9-4ba1-8061-2cc38d3e4286)

<br>

## Step 11
Now, for the final step, we try to access the DVWA through the browser in our Kali VM by simply entering the IP. If everything is correct, you will see this

![10](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/2a707f04-4b57-411b-9c1e-8634c3991a9a)

<br>


I hope this helps 
