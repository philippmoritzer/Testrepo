<title>asdfasdgasdg</title>

# Task 2 - Cloud Server

## Cloud Server using Microsoft Azure


**Student:**    Philipp Moritzer  
**Student ID:** 21170004


**Module:**               Unix System  
**Professor:**            이길흥  
**Due Date:**             6th June 2021  
**Date of assignment:**   11th May 2021

**Task:** The task of the following summary consists of selecting and registering to a free-tier Service of either Google Cloud Platform, Windows Azure or Amazon Webservice. Using this platform the goal is to install a linux operating system, access the system and use it. While using the system there should be done some practice with commands learnt at the class. (For example: Shell Programming, Java Programming, C Programming)

<div style="page-break-after: always;"></div>


## Microsoft Azure

Microsoft Azure is a Cloud Computing Service provided by Microsoft. It provides Software as a Service (SaaS), Infrastructure as a Service (IaaS) and Platform as a Service (PaaS). The Applications, Platforms and Infrastructure is run on Microsoft managed data centers.
In this special occasion Microsoft Azure is used to build a Cloud Linux Server running Ubuntu. The goal of this project is to create an accessible Linux (Ubuntu) Virtual Machine. The Virtual Machine is supposed to be accessed by Telnet or SSH. After creating the Machine it should be usable and there will be some minor practice done with commands learnt at the class.

## Setting up the Virtual Machine

To setup the Virtual Machine, the website https://portal.azure.com/ is accessed and a free account created. The next step is to create the Virtual Machine using the Wizard provided by the platform (see Figure 1 and Figure 2).    

![](../../images/2021-05-12-22-03-51.png)*Figure 1: Main Page of the Azure Portal*  
  
![](../../images/2021-05-12-22-06-41.png)  
*Figure 2: Add Virtual Machine in the VM Overview Page*  

After initalizing the Setup Wizard the Virtual Machine's properties have to be set.
<div style="page-break-after: always;"></div>

### Project Details
The section Project Details defines the cost and resource management of the Virtual Machine.  

![](../../images/2021-05-12-22-12-03.png)  
*Figure 3: Setting up Project Details*  

- Subscription: Azure for Educational Institutions
  - Defines that the free Azure Service provided for Educational Institutions is used.
- Resource Group: Linux
  - Assign a group to manage multiple Virtual Machines in one's Account.
### Instance Details
In the instance details the properties of this certain Virtual Machine will be set.
![](../../images/2021-05-12-22-14-53.png)  
*Figure 4: Setting up Instance Details*  

- Virtual Machine Name: my-ubuntu-16
  - The name of the Virtual Machine in the Azure Portal.
- Region: (US) South Central US
  - The region in which the Server will be located. It will be left on South Central US (default).
- Availability Options: Availability zone
  - Availability zone options means that the resources will be physically separated within an Azure region. 
- Availability Zone: 1
  - Set to default since it is not important in this step.
- Image: Ubuntu 16.04 LTS - Gen1
  - Defines that the Vitual Machine will run Ubuntu 16.04 Latest Stable Relase. If a Windows Virtual Machine is needed it is also possible to choose this here or any other Version of a listed Operating System.
- Azure Spot instance: Not selected
  - Makes the user pay for workload instead of time. It is not needed here since the Virtual Machine will be set on a free account.
- Size: Standard_D2_v3 - 2 vcpus, 8 GiB memory (67,72 €/month)
  - There will be 2 virtual CPUs and 8 Gigabytes of Memory assigned to this Virtual Machine. More Power is more expensive but the free budget is used here so it is not changed.

### Administrator Account
In this section it is determined how to access the server.

![](../../images/2021-05-12-22-52-56.png)  
*Figure 5: Setting up Administrator account*  

- Username: pmoritzer
  - The username to access the server, using student's id
- SSH public key source: Use existing public key
  - Generating a Public Key using the ssh-gen Windows Command-Line Tool
- SSH public key: \<ssh key>
  
To generate the Public SSH-Key following command has to be used. The result will be safed to a id_rsa.pub-File which content has to be inserted into the SSH public key field.

```bash
$ ssh-keygen -m PEM -t rsa -b 4096
```
### Inbound Port Rules
Inbound Port rules decide on which port the virtual machine can be accessed. Here only the SSH Standard Port 22 will be used.  
![](../../images/2021-05-12-22-56-56.png)  
*Figure 6: Setting up Inbound Port Rules*  

- Public inbound ports: Allow selected ports
  - Only selected ports are allowed
- Select inbound ports: SSH(22)
  - Only the standard SSH Port (22) is allowed to access the server

### Disks - Disk Type
The disk type will be set to Standard HDD to save running costs:  
![](../../images/2021-05-12-22-59-58.png)  
*Figure 7: Setting up Disks - Disk Type*  
<div style="page-break-after: always;"></div>


### Management - Monitoring
In the management Tab a monitoring account will be set up. The name is the same as the user id:  

![](../../images/2021-05-12-23-05-24.png)  
*Figure 8: Setting up Management Account*  

### Finishing the Setup
After Validating a click on "Review + create" creates the Virtual Machine and it is ready to be accessed.  

![](../../images/2021-05-12-23-19-01.png)  
*Figure 9: Finishing the Setup*  

## Accessing the Virtual Machine

To connect to the Virtual Machine the Azure Portal provides connection instructions. This time how to connect with SSH:

![](../../images/2021-05-12-23-21-08.png)  
*Figure 10: SSH Connection instruction*
<div style="page-break-after: always;"></div>

The connection using this command will be successful by providing the private key for the connection:  

![](../../images/2021-05-12-23-23-45.png)  
*Figure 11: Establishing an SSH Connection*
<div style="page-break-after: always;"></div>

## Using the Virtual Machine

### Basic Commands
Using simple Unix commands to show that the server is working:  

![](../../images/2021-05-12-23-27-54.png)  
*Figure 12: Trying out simple unix commands*  

```bash
$ sleep 600 & # start a 600 seconds sleep progress in background
$ jobs  # lists all the jobs
$ ps -ef | grep sleep # lists all the processes containing 'sleep'
$ kill -9 19940 # terminates sleep process
```  

![](../../images/2021-05-13-14-58-33.png)  
*Figure 13: Trying out job commands*  
### C Programming
Writing a simple 'Hello World' program using C Programming Language:  
```bash
$ sudo apt install gcc # installs gcc compiler for c language
$ vi hello_world.c
```  

![](../../images/2021-05-12-23-30-53.png)  
*Figure 14: Hello World C-Program*

```bash 
$ gcc -o hello_world hello_world.c # compiles program with output name hello_world
$ ./hello_world # execute hello world program
```  

![](../../images/2021-05-12-23-33-22.png)  
*Figure 15: Running Hello World C-Program*  
### Java Programming
Writing a simple Java Programm that prints an array of input strings:
```bash
$ sudo apt install openjdk-8-jdk-headless # install JDK for Java Compiling and Runnings
$ vi PrintStrings.java
```
![](../../images/2021-05-12-23-37-43.png)  
*Figure 16: Printing Argument Java Program*  
```bash
$ javac PrintStrings.java # compiles PrintStrings.java - program
$ java PrintStrings Ubuntu Debian Mint Elementary # Executes compiled Java Program with arguments
```

![](../../images/2021-05-12-23-41-22.png)  
*Figure 17: Running Printing Argument Java Program*  
### Shell Programming
Writing a simple shell programm that asks the user for the name and greets the user:  

```bash
$ vi askname.sh
```  

![](../../images/2021-05-12-23-45-41.png)  
*Figure 18: Ask name Shell Script*  

```bash
$ chmod u+x askname.sh
$ ./askname.sh
```  
![](../../images/2021-05-12-23-47-17.png)   
*Figure 19: Running Ask name Shell Script*  
### AWK
Using the AWK language to print out the average grades from students:  

```bash
vi students.txt
```  
![](../../images/2021-05-13-00-01-09.png)  
*Figure 20: Setting up students.txt data source*  

```bash
vi average.awk
```  

![](../../images/2021-05-13-14-52-30.png)  
*Figure 21: AWK Script to determine averages*  

```bash
awk -f average.awk students.txt
```  
Output:  

![](../../images/2021-05-13-14-53-28.png)  
*Figure 22: Running awk script with the data source*  