# 21/21/2025
# Account Setup
1. I began by creating a Microsoft Azure account using the email address provided by my university.
2. Next, I familiarized myself with cloud computing and its significance.
3. I also explored the benefits available to students and opened a student account, which granted me $100 in credits to use for purchasing any package within the Azure environment.
# Creating a Virtual Machine
1. I set up a virtual machine to work on later in the course.
2. I selected Ubuntu Server 24.04 LTS Gen 2, published by Canonical, from the Azure Marketplace.
3. The machine was named "lab-robotics".
4. For the configuration, I opted for the Standard_B2ls_v2 instance from the B-series.
5. Additionally, I created a new resource group and a subnet to host the virtual machine.
# Linking My HAMK Email to GitHub
I created a new repository named "linux" for the assignment.
Then, I added my HAMK email as a secondary email address for version control.
# image
![image 1](image/Screenshot%20(159).png)


# Assignment 3: User Management and File System Access


## Step 1:
- First of all I create two users named **tupu** and **lupu**.
- Then set **password** and other necessry information so that only that user can access the file.
- I userd sudo and adduser command for that.

        sudo adduser tupu

## Step 2:
- Then I create lupu user using useradd command.

        sudo useradd -m -d /home/lupu -s /bin/bash -G lupu lupu

- -m: Create the user's home directory.
- -d /home/lupu: Specify the home directory path.
- -s /bin/bash: Set the login shell to /bin/bash.
- -G lupu: Add the user to the lupu group.

## Step 3: 
- Furthermore, I create the hupu system user with the login shell set to **/bin/false** file.

       sudo useradd --system --shell /bin/false hupu

- --system: Create a system account.
- --shell /bin/false: Set the login shell to /bin/false to prevent login.

## Step 4: 
- Then I use **visudo** to edit the sudoers file

        sudo visudo

- Then add the following lines for both users:

        tupu ALL=(ALL:ALL) ALL
        lupu ALL=(ALL:ALL) ALL

- There is another method as well but I present here only the only but i run both.

## Step 5:
- I create directory in **/opt/projekti** and add both users

        sudo mkdir /opt/projekti

- Then crete a group called projekti and assign both tupu and lupu into the group and the commands are:

        sudo groupadd projekti
        sudo usermod -aG projekti tupu
        sudo usermod -aG projekti lupu

- And give ownership to projekti group.

        sudo chown :projekti /opt/projekti

- And **set permission** so that tupu and lupu can access the file in all three formate like read, write and execute files.

        sudo chmod 770 /opt/projekti

- The following command ensures that any new files created within the /opt/projekti directory inherit the group ownership of projekti, maintaining the desired permissions.

        sudo chmod g+s /opt/projekti

## Output:

        drwxrws--- 2 root projekti 4096 Jan 30 22:44 /opt/projekti


# Screenshot:

![Scheershot1](image/image.png)