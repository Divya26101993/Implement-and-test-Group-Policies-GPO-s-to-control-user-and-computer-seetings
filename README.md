## Setting Up and Testing Group Policies (GPOs) on Windows Server 2022 and Client Machines

This guide will walk you through the process of joining a computer to a domain, configuring DNS and static IPs, and implementing Group Policy Objects (GPOs) on both Windows Server 2022 and Windows 10 machines. By following these steps, you'll be able to manage and enforce security and system settings across multiple machines in your network environment

## Prerequisites

1.**Windows server installation**: Install Windows server 2022 on a virtual machine
2.**Active Directory Domain Services (AD DS)**: Install and configure AD DS to create a Domain
3.**Group Policy Management Console (GPMC)**: Install GPMC on your Windows Server to manage GPOs
4.**Windows Pro or Enterprise** :Install Windows 10 Pro or Enterprise in VM 

## Installation Steps

### Step 1:Download the Windows 10 Enterprise ISO file for use with VMware

Search for Windows 10 Enterprise ISO: Use **Google** to search for **Windows 10 Enterprise ISO** free download, then navigate to**Microsoft’s Evaluation Center** and select the **Windows 10 Enterprise Evaluation Edition**

<img width="1073" height="904" alt="Image" src="https://github.com/user-attachments/assets/3ebc0f85-913e-42d8-8068-fcd0e12a9426" />

Select the **64‑bit edition** of the Windows 10 Enterprise ISO file to ensure better performance, improved speed, and compatibility with modern hardware.The 32-bit version is outdated and slower

<img width="1710" height="943" alt="Image" src="https://github.com/user-attachments/assets/0f1737e5-7257-48fb-9ba1-6eeab99435a7" />

Once selected, the download will begin and may take a few minutes to complete. You can monitor the progress and find the ISO file in your system’s **Downloads** folder

<img width="991" height="208" alt="Image" src="https://github.com/user-attachments/assets/fa55bfcd-71b4-42d1-a718-fedaf04e9241" />

### Step 2:Install Windows 10 Enterprise on VMware Workstation

First, launch VMware Workstation and start the process to create a new virtual machine 

On the next screen, you’ll see two options: **Typical** and **Custom**. Leave the default **Typical** selected, as it’s sufficient for home lab setups and doesn’t require advanced configurations and then Click **Next**

<img width="497" height="529" alt="Image" src="https://github.com/user-attachments/assets/60801152-37da-4bf3-8b2f-5e52116f32e6" />

On the next screen, select **I will install the operating system later**. This helps avoid potential errors or issues that can occur if you try to install directly from the ISO file at this stage.Click **Next**

<img width="503" height="531" alt="Image" src="https://github.com/user-attachments/assets/dd2961db-b551-40e3-b909-23961b17e6c7" />

Next, select **Microsoft Windows** as the guest operating system, and choose **Windows 10 x64** as the version, then Click **Next**

<img width="506" height="530" alt="Image" src="https://github.com/user-attachments/assets/0fabf5e8-2116-4864-a187-dbb2a3b2f8ac" />

On the next screen, you can change the virtual machine’s name and location if you want, or leave the defaults as they are. Then Click **Next**

<img width="502" height="533" alt="Image" src="https://github.com/user-attachments/assets/f37fa85a-c908-423d-b5de-4037e2017198" />

For home lab environments, the virtual machine’s disk size can be reduced to **20 GB** to save space; however, keeping the default 60 GB allocation is also acceptable and does not impact functionality and Click **Next**

<img width="500" height="531" alt="Image" src="https://github.com/user-attachments/assets/1ba77d57-0ecb-4995-8e8f-1efc212d5b87" />

<img width="498" height="531" alt="Image" src="https://github.com/user-attachments/assets/d2dc5685-f8a5-4e9f-94a7-097e6db64fc4" />

After configuring all settings, click **Finish** to complete the virtual machine setup

<img width="499" height="528" alt="Image" src="https://github.com/user-attachments/assets/c67a73ea-510a-4020-ab0b-bda36b526b5b" />

Windows 10 Enterprise has now been successfully installed in the virtual machine

<img width="1915" height="997" alt="Image" src="https://github.com/user-attachments/assets/d2ccbdce-2fe0-46d0-9ab0-fc0d84c52ddb" />

Next, to add the ISO file to the **Windows 10 Enterprise** virtual machine, right-click the virtual machine and select **Settings**. The following window will open

<img width="895" height="904" alt="Image" src="https://github.com/user-attachments/assets/08499ed3-4064-433e-a59e-921538cc8c4c" />

In the Settings window, select **CD/DVD (SATA)** from the left pane. On the right side, choose **Use ISO image file**, then browse to select the ISO file from your Downloads folder. Finally, click **OK** to confirm

<img width="891" height="903" alt="Image" src="https://github.com/user-attachments/assets/3d4a6a2c-c25e-49f7-9f99-5be354415b8b" />

<img width="949" height="474" alt="Image" src="https://github.com/user-attachments/assets/1511b3a8-68c1-4eb4-adaa-0bd41d6cfd60" />

<img width="893" height="900" alt="Image" src="https://github.com/user-attachments/assets/d383b471-3a34-4f63-a1f3-985fd42b9da7" />

Now, power on the virtual machine to begin the Windows installation

<img width="689" height="191" alt="Image" src="https://github.com/user-attachments/assets/76164e97-2934-4b44-818c-ec3860e8675b" />

The following screen will display the language options for installing Windows. Leave it as the default language and click **Next**

<img width="620" height="462" alt="Image" src="https://github.com/user-attachments/assets/c8f1ee72-ff8b-43ca-aa36-21986e24b2a8" />

On the next screen, click **Install Now**

<img width="623" height="448" alt="Image" src="https://github.com/user-attachments/assets/3f62379f-7027-4f58-8735-9850c1c49d7b" />

Check the box to accept the terms and click **Next**

<img width="1035" height="772" alt="Image" src="https://github.com/user-attachments/assets/9e9220a3-9b20-482d-a1a0-c5f05b536c77" />

Since we're installing Windows on a new virtual machine, not upgrading, select **Custom** installation

<img width="643" height="478" alt="Image" src="https://github.com/user-attachments/assets/9892b70b-1297-41c2-8b92-c8c9c8715ab5" />

On the next screen, you'll see the drive partitions. Since we only have one drive, simply click **Next** to proceed with the installation

<img width="640" height="485" alt="Image" src="https://github.com/user-attachments/assets/de4ba43e-a202-4f6e-9f56-03bd1ed0a173" />

Now, Windows will start installing. This process may take some time, so just let it run

<img width="643" height="483" alt="Image" src="https://github.com/user-attachments/assets/aec5981f-7cf3-4f17-8847-8a1bd7f261c7" />

Once the installation is complete, you'll be prompted to select your region. Choose the appropriate region and click **Yes**

<img width="1032" height="677" alt="Image" src="https://github.com/user-attachments/assets/9818278e-b9c5-4d67-9687-e6e8f67531e0" />

Since we're adding a user to a domain, select the **Domain join Instead** option instead of setting up a  Microsoft account

<img width="1035" height="723" alt="Image" src="https://github.com/user-attachments/assets/7d6adf31-15f5-4333-ba35-ed471e004d88" />

Next, create a username for the PC and click **Next**

<img width="1026" height="678" alt="Image" src="https://github.com/user-attachments/assets/da059577-9981-4e4b-9258-4c23a87bd55c" />

On the next screen, create a memorable password and click **Next**

<img width="1027" height="723" alt="Image" src="https://github.com/user-attachments/assets/20992b55-216f-4103-bb80-607f8f06a366" />

Re-enter the same password on the next screen and click **Next**

<img width="1029" height="718" alt="Image" src="https://github.com/user-attachments/assets/2d85db66-6da8-4117-a9d3-e949c1f9210d" />

Next, choose and answer three security questions from the pre-set options, ensuring you select answers you'll remember, then click **Next**

<img width="1032" height="725" alt="Image" src="https://github.com/user-attachments/assets/c7f09a9f-001e-40c5-95a4-c020295392ec" />

On the privacy settings screen, all options are enabled by default. You can adjust them based on your preferences, but we'll leave everything as is and click **Accept**

<img width="1029" height="774" alt="Image" src="https://github.com/user-attachments/assets/8791329a-f51a-4583-9ee6-b8413cac3e73" />

On the next screen, simply click **Accept**

<img width="1027" height="716" alt="Image" src="https://github.com/user-attachments/assets/b56361f5-02a4-4988-a32b-253f8cdc4fe1" />

This may take a few minutes to apply all the settings. Once it's complete, you'll be directed to the desktop

<img width="1031" height="771" alt="Image" src="https://github.com/user-attachments/assets/7be7edf8-d8f3-4b60-bb5d-3ea968d1f066" />

Finally, you'll see Windows Enterprise, and you can use it for a 90-day trial period

<img width="1021" height="737" alt="Image" src="https://github.com/user-attachments/assets/117d9182-6589-4741-91e1-296ae289c0f0" />

### Step 3: Configure DNS Server in Windows Server 2022 and Assign Static IP to the Server

Before joining a Windows machine to the Windows Server domain, we need to configure the DNS server and assign a static IP to the server. The client machine joining the domain will then use this static IP as its DNS server.

Configuring a static IP ensures the server maintains a consistent address, preventing network disruptions and ensuring reliable DNS resolution, domain joining, and remote management.
First, shut down the Windows Enterprise machine and power on the Windows Server virtual machine

<img width="819" height="270" alt="Image" src="https://github.com/user-attachments/assets/aedccd69-4188-4ed0-8048-f298f47b85d5" />

In my previous repositories, I've already set up the domain and configured the GPOs, so I can sign in directly as an admin

<img width="1417" height="822" alt="Image" src="https://github.com/user-attachments/assets/c8f59653-d981-4e40-8aa9-4a45b7025441" />

Instead of configuring a random static IP for the domain controller, always verify the IP address assigned by the ISP. To do this, open the ?**Command Prompt** and use the **ipconfig** command to view the current network configuration

<img width="765" height="162" alt="Image" src="https://github.com/user-attachments/assets/6db217b9-96ff-4bdf-8525-89649aae6a13" />

In the screen below, you can see the IPv4 address of the domain controller

<img width="980" height="515" alt="Image" src="https://github.com/user-attachments/assets/22196d9a-d5ff-44c1-ac93-58bf419d2794" />

Now Go to the network icon in the right-hand corner of the taskbar and select **Open Network & Internet Settings**

<img width="1061" height="797" alt="Image" src="https://github.com/user-attachments/assets/73a1e2c1-1cfd-4f8b-9db5-43771f17ddda" />

On the next screen, select **Change adapter options**

<img width="806" height="640" alt="Image" src="https://github.com/user-attachments/assets/c0f956df-d3d8-49f7-9a6d-181932b8c4d2" />

You will see your network connections. Select **Ethernet**, right-click on it, and choose **Properties**

<img width="788" height="592" alt="Image" src="https://github.com/user-attachments/assets/e512ccae-c4ba-4d22-a2c9-def9122678c6" />

Since we're configuring a static IP, click on **Internet Protocol Version 4 (TCP/IPv4)**

<img width="366" height="466" alt="Image" src="https://github.com/user-attachments/assets/a9c3d0e1-aaab-420c-ade0-117eeac1f7ef" />

On this screen, you will see the DNS server options

<img width="404" height="458" alt="Image" src="https://github.com/user-attachments/assets/3a7cec70-84c0-4ffe-9dcb-377349630118" />

Enter the IPv4 address, subnet mask, and default gateway that you verified earlier using the ipconfig command in Command Prompt

<img width="401" height="454" alt="Image" src="https://github.com/user-attachments/assets/318350a7-a098-4ded-aa25-0dd70afaef7d" />

In most configurations, the domain controller’s loopback address 127.0.0.1 is set as the primary DNS server. This is because the domain controller also serves as the DNS server for the domain, and internal name resolution relies on this address. Click **OK**

<img width="399" height="455" alt="Image" src="https://github.com/user-attachments/assets/29b3cc33-3834-44a9-bfd3-993dc745508f" />

### Step 4: Check Domain Controller DNS Server Address

Open **Command prompt**  and type **ipconfig /all** command 

<img width="693" height="463" alt="Image" src="https://github.com/user-attachments/assets/73cedbb8-a3aa-475f-99d8-0ed8b6f02f6b" />

Now that we’ve successfully set up the Windows Server with all the necessary configurations, power on the client Windows machine.

### Step 5: Configuring DNS on the client machine to point to the domain controller for domain joining

First, power on the Windows 10 Enterprise client machine

<img width="1636" height="946" alt="Image" src="https://github.com/user-attachments/assets/9c837492-37c9-4c25-aef2-30ff9491c458" />

**Open Network  & Internet settings -> change  adapter Options -> Ethernet -> Properties -> Internet Protocol Version 4 (TCP/IPv4)**

<img width="920" height="727" alt="Image" src="https://github.com/user-attachments/assets/41c6a682-26f9-4523-99b8-9b30a1f005d9" />

We will leave the client machine's IP configuration as Dynamic (DHCP), and configure the Windows Server's static IP address as the DNS server on the client machine, Then click **OK**

This ensures that the client machine uses the domain controller's DNS for domain resolution

<img width="399" height="454" alt="Image" src="https://github.com/user-attachments/assets/a807e02e-38fc-447c-8162-d351d1a4c7c7" />

<img width="403" height="459" alt="Image" src="https://github.com/user-attachments/assets/f31537c0-676b-493e-a3e1-cba5606232b0" />

### Step 6: Verify the Client Can Ping the Domain Controller

In **Command Prompt**, type the following command to ping the domain controller (Windows Server) with its static IP: **ping 192.168.43.134**

This will check if the client machine can successfully communicate with the domain controller using its static IP address. If successful, you will see replies from the server

<img width="979" height="517" alt="Image" src="https://github.com/user-attachments/assets/2d4a01d8-23e8-4a92-ab34-88f3e0828d0c" />

As per the results, the client has successfully pinged the server, confirming that the network connection between the client machine and the domain controller is working properly

This test helps ensure that the client machine can communicate with the domain controller over the network. If the ping fails, troubleshoot the network connectivity or firewall settings

### Step 6: Joining the Client Machine to the Domain and use user accounts in Active directory

Open **File Explorer**, right-click on **This PC**, select **Properties**

<img width="791" height="618" alt="Image" src="https://github.com/user-attachments/assets/88573c95-471d-459f-a2c4-9c936efbd707" />

On the next screen, select Rename this PC (Advanced) on the right-hand side

<img width="1027" height="734" alt="Image" src="https://github.com/user-attachments/assets/132f9284-56dd-4245-b5d5-eb950fa34948" />

In the screen below, select Change

<img width="413" height="468" alt="Image" src="https://github.com/user-attachments/assets/ec353686-9ffe-46da-99c2-55e137e4254b" />

If you want to change the computer name, you can do it here. Then, select **Domain**, and type the domain name **IT.local** (or your specific domain name), then Click **OK**

<img width="321" height="392" alt="Image" src="https://github.com/user-attachments/assets/d2955996-9127-4255-a434-5ebcf348eed7" />

<img width="326" height="397" alt="Image" src="https://github.com/user-attachments/assets/2f17daa3-2aef-4f18-8e5b-4318bfd8e6b4" />

Next, type the Administrator username and password, then click **OK**

<img width="455" height="299" alt="Image" src="https://github.com/user-attachments/assets/6a8e4752-fa7f-4ab6-bcbd-15358c4e357e" />

Now, you should see a window displaying "Welcome to the domain", confirming that the client machine has successfully joined the domain, Click **OK**

<img width="269" height="157" alt="Image" src="https://github.com/user-attachments/assets/79f57c22-6c0b-44fa-ad20-8d2aaffab19d" />

After that, Windows will prompt you to restart the machine to apply the changes and complete the domain join process

<img width="353" height="185" alt="Image" src="https://github.com/user-attachments/assets/66ddee12-41de-43e3-ae5d-42ceeee5f61e" />

Once the machine restarts, you will see two options: User1 (the local account). Click on Other User to log in with a domain account

<img width="1028" height="766" alt="Image" src="https://github.com/user-attachments/assets/6700493c-d13e-41b5-b6db-c9bba8549071" />

In this step, we will use the user accounts that were created earlier in Active Directory to log in

<img width="1028" height="766" alt="Image" src="https://github.com/user-attachments/assets/38608e71-4c12-4116-b22a-c5499d20cab3" />

Go to **Active Directory Users and Computers**, select **IT.local -> UK -> Users**. On the right-hand side, you will see the user accounts that were already created

<img width="757" height="536" alt="Image" src="https://github.com/user-attachments/assets/24233632-7690-4fd6-873a-ccc2dc962296" />

Type the username and password for the domain account, then click OK to complete the process of joining the client computer to the Active Directory domain

<img width="1028" height="776" alt="Image" src="https://github.com/user-attachments/assets/77b0c799-bacd-4018-959f-3921d5c098b7" />

Now, the computer has successfully joined the domain, and you can use the user accounts that were created in Active Directory to log in

### Step 7:Implementing and Testing GPO's in Client machine

First, go to the **Windows Server** where you have Active Directory and Group Policy Objects (GPOs) configured

Go to the Group Policy Management Console (GPMC) where you can see the Group Policy Objects (GPOs) that were created earlier Repositories

<img width="1025" height="706" alt="Image" src="https://github.com/user-attachments/assets/4d464c60-7442-44b9-986b-69b51d4258d8" />

Drag and drop the GPOs to the appropriate Organizational Unit (OU) where you want to implement them.

<img width="1028" height="706" alt="Image" src="https://github.com/user-attachments/assets/1ff2da20-43c3-4915-94c4-ae3be22da13b" />

<img width="1032" height="730" alt="Image" src="https://github.com/user-attachments/assets/feb53795-7402-486a-88ec-6c34458a7159" />

Once the domain is joined, the newly joined computer will automatically appear in the **Computers** folder within **Active Directory Users and Computers**

<img width="755" height="533" alt="Image" src="https://github.com/user-attachments/assets/c039ddc3-5072-4927-8208-6ce67dd6e6e1" />

Now, move the computer to its respective OU. To do this:

Right-click on **COMPUTER1**

Select **Move**

Choose the respective OU and click **OK**

Once you refresh the view, you will see the computer in the selected OU

<img width="759" height="510" alt="Image" src="https://github.com/user-attachments/assets/edec294d-9070-4a9f-ad53-49dfb06be91d" />

<img width="322" height="327" alt="Image" src="https://github.com/user-attachments/assets/f1e51010-f4ba-4153-994b-c3d6776e02e7" />

<img width="759" height="532" alt="Image" src="https://github.com/user-attachments/assets/04ab17c5-f5f4-4f5b-864e-6d528a4b5ef1" />

If you want to add a description to the computer, click on COMPUTER1, then go to the Description field and add the information as per your reference

<img width="469" height="513" alt="Image" src="https://github.com/user-attachments/assets/0f9d3f7e-66c7-47c4-83f2-6ae91f32f4fe" />

<img width="464" height="512" alt="Image" src="https://github.com/user-attachments/assets/9e8af046-02aa-44b5-b4bf-d4b74a20fe50" />

We are testing the Restrict Control Panel GPO on the **client machin**e. When you try to **open the Control Panel**, it will show the error: **This operation has been canceled due to restrictions in effect on this computer**




























