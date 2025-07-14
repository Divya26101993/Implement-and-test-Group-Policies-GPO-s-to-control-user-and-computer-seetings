## Implement and Test Group Policies (GPOs) to Manage User and Computer Settings

A step-by-step guide to joining a computer to a domain and applying Group Policy Objects (GPOs)

## Prerequisites

1.Windows server installation: Install Windows server 2022 on a virtual machine
2.Active Directory Domain Services (AD DS): Install and configure AD DS to create a Domain
3.Group Policy Management Console (GPMC): Install GPMC on your Windows Server to manage GPOs
4. Windows Pro or Enterprise :Install Windows 10 Pro or Enterprise in VM 

## Installation Steps

### Step 1:Download the Windows 10 Enterprise ISO file for use with VMware

Visit Google and search for “Windows 10 Enterprise ISO free download,” then navigate to Microsoft’s Evaluation Center and select the Windows 10 Enterprise evaluation edition

<img width="1073" height="904" alt="Image" src="https://github.com/user-attachments/assets/3ebc0f85-913e-42d8-8068-fcd0e12a9426" />

Select the 64‑bit edition of the Windows 10 Enterprise ISO file to ensure better performance, improved speed, and compatibility with modern hardware.

<img width="1710" height="943" alt="Image" src="https://github.com/user-attachments/assets/0f1737e5-7257-48fb-9ba1-6eeab99435a7" />

Once selected, the download will begin and may take a few minutes to complete. You can monitor the progress and find the ISO file in your system’s Downloads folder

<img width="991" height="208" alt="Image" src="https://github.com/user-attachments/assets/fa55bfcd-71b4-42d1-a718-fedaf04e9241" />

### Step 2: Install Windows 10 Enterprise on VMware Workstation

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

Once the installation is complete, you'll be prompted to select your region. Choose your appropriate region and click **Yes**

<img width="1032" height="677" alt="Image" src="https://github.com/user-attachments/assets/9818278e-b9c5-4d67-9687-e6e8f67531e0" />

Since we're adding a user to a domain, select the **Domain join Instead** option instead of setting up a  Microsoft account






