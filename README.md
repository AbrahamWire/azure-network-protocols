<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h1>Part 1: Create a Resource Group as well as your first VM</h1>
<p>In Azure create a Resource Group and name it "whatever-RG"</p>

![network1](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/c2cb7dd0-970f-42aa-93dd-0269dfe62e89)

<p>Create a Windows 10 Virtual Machine and name it "VM1". Don't forget to choose the resource group you just created.</p>

![network2](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/26600670-3065-4746-9a5b-51ed6130f1ec)

![network3](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/b42cb325-8e1f-4f53-a5b2-d1abcee6ec9e)

<h1>Part 2: Create the second Virtual Machine</h1>

<p>Once the first VM is FULLY created start creating your second VM</p>
<p>Choose the same resource group and name this VM "VM2" and choose ubuntu server 20.04 LTS. Make sure to click password on Authentication type.</p>

![network4](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/bab04770-9cc0-41f2-858c-0cde522905d8)

![network5](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/a15a62f1-3692-4c6e-9dcb-880ee07377ab)


<p>In Networking choose the same Virtual Network as "VM1". It should be called "VM1-vnet" (If it's not there then VM1 is still not FULLY created. It take a few minutes)</p>

![network6](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/8ad44de8-c788-4ad0-8c30-ac2bd63f5e9e)

<h1>Part 3: Sign into "VM1" and download Wire Shark</h1>

<p>Open up Remote Desktop and sign into "VM1" using its IP address open the web browser and download Wire Shark</p>

![network7](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/6af260e2-7bc6-48c8-8a94-19498ef31ede)

![network8](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/33b8126d-1d63-4c5d-89e3-f26e0ff6e9f4)

<h1>Open up Wire Shark and observe ICMP traffic</h1>

<p>In Wireshark filter for ICMP traffic.</p>

![network9](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/bdee6d03-36ce-46bd-8ce8-ebe140d6c7a3)

<p>Open up command tool and attempt to ping your Ubuntu machine(Get the private ip address from Azure) and observe</p>

![network10](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/451b5826-c454-4963-b269-cb019f93f4ab)

![network11](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/010b5709-16b7-46ec-ad3e-7de91f06f17c)

<p>Initiate a non stop ping to your Ubuntu machine</p>

![network12](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/f079efc3-8b11-4b10-8b65-7498dfc42aa2)

<p>Go back to Azure and in Network Security Groups disable any incoming ICMP traffic</p>

![network13](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/eb810331-9266-4b89-b8ec-efcd1d33e5de)

<p>Observe the traffic back in "VM1"</p>

![network14](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/126792ce-0296-4c59-86da-bdf399fab91f)

<p>Go back to Azure and re-enable ICMP traffic and observe your VM once again</p>

![network15](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/73c290ac-85e0-43e1-8b08-8caf7096de9a)

![network16](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/4a4e3e10-65f7-49fc-b9a7-0a7a81aacb0d)

<p>Hit Control+C to stop the traffic completely</p>
<h1>Part 4: Observe SSH traffic</h1>
<p>Filter for SSH traffic then in Command line ssh into your Ubuntu machine. Type yes then enter your "VM2" password</p>

![network17](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/8178dbc5-50ed-4cfb-bb3e-44b893c9267c)

<p>Google some command lines for linux and mess around with it. Then exit the machine.</p>

<h1>Part 5: Observe DHCP traffic</h1>
<p>In Wire Shark filter for DHCP traffic</p>
<p>In command line issue yourself a new IP address</p>

![network18](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/d42ea2f0-4e87-4929-8327-fac61d68d389)

<h1>Part 6: Observe for DNS traffic</h1>
<p>In Wireshark filter for DNS traffic</p>
<p>Type nslookup in Command line as well as any website you choose and observe</p>

![network19](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/d56ae0cc-2518-4ec5-96de-9b83bef5f8b0)

<h1>Part 7 :Observe for RDP traffic</h1>
<p>In Wire Shark filter for RDP (tcp.port == 3389) and observe</p>

![network20](https://github.com/AbrahamWire/azure-network-protocols/assets/155400161/bcfb8dbd-8a67-47b8-bf5a-51d1178f1081)


<h1>Conclusion</h1>
<p>And thats all! Now you learned a little about protocols and what information is shown! Make sure to look at other information online and continue to leanr!</p>
