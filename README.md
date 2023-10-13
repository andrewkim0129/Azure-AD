# Building an OpenVAS Vulnerability Management Lab
![image](https://github.com/andrewkim0129/Azure-AD/assets/27276227/3607402f-4ed0-4136-b2f7-7b1a54c1d6f1)


## Introduction

In this project, I built an Azure home lab involving a vulnerable VM client and OpenVAS, a vulnerability scanner, to conduct security scans. The scan results helped identify vulnerabilities, allowing for targeted remediation actions.




## Deploying Vulnerability Management Scanner 

After the OpenVAS VM was deployed under the pre-defined role group, SSH into this VM as admin.

![image](https://github.com/andrewkim0129/Azure-OpenVAS/assets/27276227/bbfebf54-2580-4520-ab18-7b0e734610ce)

Accessed the web interface by using the Openvas URL shown after the installation 

![image](https://github.com/andrewkim0129/Azure-OpenVAS/assets/27276227/57871508-c288-4809-8e69-bdcb8fff874d)




## Deploying a Client Virtual Machine and Making it Vulnerable

Created a win10 VM under the same RG and vnet to make vulnerable

![image](https://github.com/andrewkim0129/Azure-OpenVAS/assets/27276227/7ef6034f-da4a-4548-a99a-72cfa707f5ad)

This was achieved by introducing two vulnerabilities at the system (Firewall) and application level (outdated software) 

![image](https://github.com/andrewkim0129/Azure-OpenVAS/assets/27276227/3ab9d650-4178-4a1e-9071-543193f78719)
![image](https://github.com/andrewkim0129/Azure-OpenVAS/assets/27276227/3125585c-65ea-4627-be78-b33cf67e85fe)




## Configuring OpenVAS for the Initial Unauthenticated Scan against the Vulnerable VM

Logged into OpenVAS → Assets → Hosts → New Host with the Client VM's private IP Address

![image](https://github.com/andrewkim0129/Azure-OpenVAS/assets/27276227/95bc5f0e-40e7-4eb7-bf05-886049045002)

Created a New Target from the Host

![image](https://github.com/andrewkim0129/Azure-OpenVAS/assets/27276227/066af81b-5237-4780-baee-57593f943878)

Created a new Task

![image](https://github.com/andrewkim0129/Azure-OpenVAS/assets/27276227/e729bab4-a79c-4df2-af6f-b4cf8b363387)

Scan Completed

![image](https://github.com/andrewkim0129/Azure-OpenVAS/assets/27276227/ea010717-47a2-43fb-bc5d-90359fa97707)
![image](https://github.com/andrewkim0129/Azure-OpenVAS/assets/27276227/8ac95406-37fd-490e-a450-1fa564345945)




## Configuring OpenVAS for the Authenticated Scan against the Vulnerable VM

RDP into the Vulnerable VM to enable remote registry

![image](https://github.com/andrewkim0129/Azure-OpenVAS/assets/27276227/ab4ab3e9-140a-4409-b33a-8dbf1e25f0f7)

Navigated back to OpenVAS web interface for an Authenticated Scan Setup
New Credentials made with the admin profile

![image](https://github.com/andrewkim0129/Azure-OpenVAS/assets/27276227/559a0deb-4894-49af-97d7-d2d5c201d381)

Target made from earlier cloned and SMB set to use the credential above

![image](https://github.com/andrewkim0129/Azure-OpenVAS/assets/27276227/9d1f0a6c-1309-49ca-809c-8e90c2896889)

Cloned Task that was originally made for the unauthenticated scan, but set with the Target made above

![image](https://github.com/andrewkim0129/Azure-OpenVAS/assets/27276227/42c310e2-54b0-442a-b482-f58626183a9d)

Scan Completed

![image](https://github.com/andrewkim0129/Azure-OpenVAS/assets/27276227/a73d4ecc-5907-4924-89b2-be37578dfe98)
![image](https://github.com/andrewkim0129/Azure-OpenVAS/assets/27276227/22198ae2-53fb-499c-8715-51acbb038872)




## Remediation by Uninstalling the Applications

Uninstalled Adobe Reader, VLC Player, and Firefox on the Vulnerable client VM

![image](https://github.com/andrewkim0129/Azure-OpenVAS/assets/27276227/05996c4c-61ee-4850-9f9f-a4822827520e)




## Verifying Remediations

Ran the same scan again with a lower severity level showing after the remediation

![image](https://github.com/andrewkim0129/Azure-OpenVAS/assets/27276227/475b2114-c5fa-4314-bc72-229a0403cb4a)

Showing significantly less amount of Application related vulnerabilities

![image](https://github.com/andrewkim0129/Azure-OpenVAS/assets/27276227/9e3b73f1-c3da-4cc1-ac09-047f7bbceb29)


