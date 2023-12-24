# Connection 

Hello im going to show you how to set up your virtual machines in the same network so they are able to comunicate with each other
Im going to do it right now with Vmware Workstation pro 17

<code>Vmware Workstation pro 17</code>

We will have 1 Kali that is going to be attacker and 1 DVWA that is known for its vulnerabilities 

The Kali will have access to internet and to the DVWA, while the DVWA will only have connection to the kali

- **1-** We have to make a virtual network in the one we are going to have all our devices that are going to comunicate with each other, so we go to ***edit*** and then to ***Virtual Network Editor***

![1](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/f95d0cbb-c326-4ebf-8477-7ab6b70c9b49)

- **2-** we will see the editor with all the conections already there by default, so we click on ***add Network***

![2](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/2e18d8bb-edf2-4aa0-8baf-154bc7543567)

- **3-** we choose any of the default names and click ok

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/a9b67bfa-41a1-43fd-bb27-ab83eb5b4656)


- **4-** You can rename the network so its easier to find in this case i will name it Nat-Network, make sure that ***Host-Only*** option is selected 

![3](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/48f1cfc9-a31d-474e-8e00-8b9108275b28)

- **5-** Now we change the Subnet Ip and mask to any you want to use, in my case im using a 192.168.1.0/24, the option DHCP will specify a the range or lease times, im just changing the starting IP address so the firts host will start with x.x.x.1 

![4](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/e42ef964-1af7-48c8-9b17-38faa39e431d)

- **6-** Now we go back to the main menu and select the firts VM and click on ***Edit Virtual Machine Settings***, in my case i will use a DVWA VM that will only have 1 network adapter cause is not necessary for this VM to have internet connection

![5](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/76fdf027-241c-47df-8cc4-75ef9820869d)

- **7-** In the ***Hardware*** Tab we click on ***Network Adapter*** and change the ***Network Connection*** to Custom and Specify the name of the ***Virtual Network*** we created

![6](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/d6203a45-e2b2-4d41-be72-231ec7e2b424)

**8-** Since we are going to give this Vm access to internet, we need to add one more network adapter, cause the one it already has is the one allowing the Vm to connect to internet, we go to VM options and in ***hardware tab*** click on ***Add...*** and choose ***Network Adapter*** then click ***Finish***, this will create a ***Network Adapter 2*** that we will have to configure to our custom ***Nat-Network*** like we did in the example DVWA

![7](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/1c325c17-de2e-4c74-95d4-561a5b90a321)

**9-** after its done the Kali will look like this

![8](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/59718fa7-17ba-45c8-a37b-bdf389421ddf)

**10-** Now its time to check if both of the Vms can comunicate with each other, we open both of them and do a ***ifconfig*** so we can see what ip each one has, the ***192.168.1.105 for the DVWA*** and the ***192.168.1.1 for the Kali***, we do a ping on both of them and see if we get a reply.
As we can see the both have comunication 

![9](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/7a51e9bd-32f9-4ba1-8061-2cc38d3e4286)

**11-** Now the last part we try to access the DVWA throught the browser in our Kali vm by just entering the ip, if everything was correct you will see this.

![10](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/2a707f04-4b57-411b-9c1e-8634c3991a9a)


I hope this helps 
