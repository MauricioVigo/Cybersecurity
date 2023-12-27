# Volatility 2.6
In this guide we are going to explain how volatility 2,6 works

>[!NOTE]
>If you dont have Volatility install you can download it from here <code>[Volatility 2,6](https://www.volatilityfoundation.org/26)</code>

### What is Volatility
Volatility is a forensics framework that can be used to analyze memory dumps, it is useful in forensics and incident response tasks to extract information from the volatile memory of a running computer.

Some of the things you can do with Volatility are:

- Gathering evidence
- Investigating security incidents:
- Malware analysis:
- Sockets and connection analysis
- Process,DLL and Handles analysis
- Registry Analysis
- Create a Timeline of the attack

###  Help and Info
With Volatility <code>--info</code> two usefull things we are going to see is all the profiles that we are going to be able to use and the list of all the plugins  

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/969a2475-fdfc-4d40-aa9d-b5154c383e86)
![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/c72a1e81-3276-48c7-b7b0-1d92093ae152)

<br>

Another way to see the plugins and also the general Commands Volatility accepts is to use <code>-h</code>

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/825dc5bd-e665-4bf0-a44e-5a7be7aa5a9d)

### How to use

Firts after you have your dump file, we need to identiy what type of profile we have to use, so we use volatility and specify the route of your file and then use <code>imageinfo</code>, and its going to give you suggested profiles that are going to be able to use.

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/78dc41a5-449c-4d10-8e5e-aa4e787c15c5)

Now knowing the profile we can use -h again and see what options and plugins apply to this profile.

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/7da7dfb1-fc91-4a61-8178-9c158d352205)


