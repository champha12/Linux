# Champha Thapa

# APT Package Management Assignment

## Part 1: Understanding APT & System Updates

### 1. Check APT Version
sh
apt --version

Output:
![Version](image/version.png)

### 2. Update the Package List
sh
sudo apt update

Explanation:  
This command fetches the latest package information from the configured repositories, ensuring that the system has the most up-to-date metadata before installing or upgrading packages.

### 3. Upgrade Installed Packages
sh
sudo apt upgrade -y

*DCfference between update and upgrade:*  
- update refreshes the package metadata but does not install or upgrade anything.
- upgrade installs newer versions of the packages based on the updated metadata.

### 4. View Pending Updates
sh
apt list --upgradable

Pending Updates:  
![upgradable](image/upgradable.png)

## Part 2: Installing & Managing Packages

### 1. Search for a Package
sh
apt search image editor

Selected Package:  

![image editor](image/imageEditor.png)

### 2. View Package Details
sh
apt show zim

Dependencies:  
![Package](image/zim.png)

### 3. Install the Package
sh
sudo apt install zim -y

Confirmation of Installation:  
![install](image/install.png)

### 4. Check Installed Package Version
sh
apt list --installed | grep zim

Installed Version:  
![](image/grep.png)



## Part 3: Removing & Cleaning Packages

### 1. Uninstall the Package
sh
sudo apt remove zim -y

Is the package fully removed?  
![remove](image/remove.png)

### 2. Remove Configuration Files
sh
sudo apt purge zim -y

![Purage](image/purage.png)

*Difference between remove and purge:*  
- remove only deletes the package binaries, keeping configuration files.
- purge deletes both binaries and configuration files.

### 3. Remove Unnecessary Dependencies
sh
sudo apt autoremove -y

![Autoremove](image/autoremove.png)

Why is this step important?  
It removes unused dependencies that were installed alongside a package but are no longer needed, freeing up disk space.

### 4. Clean Up Downloaded Package Files
sh
sudo apt clean


What does this command do?  
It deletes all downloaded .deb files from /var/cache/apt/archives, freeing up space.


## Part 4: Managing Repositories & Troubleshooting

### 1. List APT Repositories
sh
cat /etc/apt/sources.list

Observations:  
![Source](image/sources.png)

### 2. Add a New Repository
sh
sudo add-apt-repository universe
sudo apt update

![universe](image/universe.png)

Types of Packages in Universe Repository:  
Community-maintained software, which may not receive the same level of support as main repository packages.

### 3. Simulate an Installation Failure
sh
sudo apt install fakepackage

Error Message:  
![fakepackage](image/fakepackage.png)

### 4. Troubleshooting Steps
- Check the package name spelling.
- Ensure the correct repository is enabled.
- Run sudo apt update and try again.
- Search for the package using apt search.
- Check logs in /var/log/apt/.

---

## Bonus Challenge: Holding & Unholding Packages

### 1. Hold a Package
sh
sudo apt-mark hold zim

![hold](image/hold.png)

### 2. Unhold a Package
sh
sudo apt-mark unhold zim

![hold](image/unhold.png)

Why would you want to hold a package?  
This prevents the package from being upgraded.

Why would you want to unhold a package?
This allows the package to be upgraded again.

# Champha Thapa
2/19/2025
Virtualization
# Part 1: Introduction to virtualization concepts
* Virtualization: the procedure for building a virtualized copy of a resource, such an operating system, storage device, or machine.
* Hypervisor: software that makes it possible to create and administer virtual machines (VMs), which let several operating systems operate on one physical computer.
* Virtual machines (VM): It's a technology for building virtualized computing environments. A virtual machine is an emulation of a physical computer. VMs enable teams to run what appear to be multiple machines, with multiple operating systems, on a single computer.
* Containers: Containers are a lighter-weight, more agile way of handling virtualization—since they don’t use a hypervisor.It is an isolated environments that run applications with shared system resources.
* The main differences between VMs and tanks: containers allow developers to improve CPU and memory utilization of physical machines. However, containers go even further because they also enable microservice architectures, where application components can be deployed and scaled more granularly. This is an attractive alternative to having to scale up an entire monolithic application because a single component is struggling with load.
* Main difference: VMs run a full OS with a virtualized hardware layer, whereas containers share the host OS kernel. VMs are more resource-intensive due to their need for dedicated system resources, while containers are more lightweight. VMs provide strong isolation due to separate OS instances; containers share the host OS, offering less isolation.