![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/8f84cc87-8dac-46e4-b032-ef5e77b7b15b)# Volatility 2.6
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

Now knowing the profile we can apply it with <code>--profile=PROFILE</code> and use -h again and see what options and plugins apply to this profile.

![image](https://github.com/MauricioVigo/Cybersecurity/assets/95547003/7da7dfb1-fc91-4a61-8178-9c158d352205)

Now after we have the profile set, we can use all the different plugins depending on your needs

### Pslist

`./volatility -f FILE --profile=PROFILE pslist` With this plugin we can show the list of processes that were running on the system at the time of the memory acquisition.

### Pstree

`./volatility -f FILE --profile=PROFILE pstree` Creates a tree-like representation of the processes running in the memory and stablishes the relationships between them, is usefull to see the parent and the child process when its needed 

### Psscan
`./volatility -f FILE --profile=PROFILE psscan` The purpose of psscan is to identifying concealed or unlinked processes that may not be shown when using the other plugins, and searches memory for process structures so it can detect processes that are hidden by malware or rootkits.

### Dlllist 

`./volatility -f ../1.vmem --profile=Win7SP1x64 dlllist`  We can use this pluging to list all the loaded DLL that are in our memory dump. DDL are shared libraries that contain code and data that multiple programs can use simultaneously, the main use of a DLL is to share content between applications and processes.

### Ldrmodules 
`./volatility -f ../1.vmem --profile=Win7SP1x64 ldrmodules` ***ldrmodules*** gathers the information about loaded dlls it has 1 column for each of the three PEB lists InLoadOrderModuleList, InMemoryOrderModuleList and InInitializationOrderModuleList  witch is ***true*** or ***false*** depending if a DLL with the same base address is already on the list, this is very helpfull to idenfity Dlls that are unlink from the ***PEB (ProcessEnvironmentBlock)*** that is a common practice to try to hide malware.

### Handles


