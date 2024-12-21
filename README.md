<p align="center">
<img src="https://github.com/user-attachments/assets/e16ec164-e5ae-4069-8476-dfc5b3e3f8bd" alt="Azure Banner"/>

</p>

<h1>Configuring Active Directory within Azure VMs</h1>
This tutorial outlines the implementation of an active directory using Microsoft Azure.<br />


<!-- <h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com) -->

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
- Windows Server

<h2>List of Prerequisites</h2>

- Create a Virtual Machine to work as a Domain Controller (called "dc-1")
- Create a Virtual Machine to work as a Client (called "client-1")
- Set dc-1 (Domain Controller) IP Address to Static
- Set client-1 DNS as the Domain Controller's private IP address
- From client-1, ping dc-1's private IP Address to ensure connectivity
- Ensure that client-1's DNS is dc-1's IP address
- Add Active Directory Domain Services to dc-1
- Promote dc-1 to a Domain Controller
- Sign in to client-1 and add it to the Active Directory domain.
- Set Group Policy

<h2>Installation Steps</h2>

<p>
<img width="1471" alt="Screenshot 2024-12-18 at 8 25 15 PM" src="https://github.com/user-attachments/assets/a8ada0d1-2e53-4d13-9cca-2998603c7fff" />

</p>
<p>
First, I created a virtual machine to work as a Domain Controller. I named it "dc-1." The operating system used was a "Windows Server." So, not only was it a Windows machine, but it also had capabilities that other machines didn't have.
</p>
<br />

<p>
<img width="1487" alt="Screenshot 2024-12-18 at 8 37 45 PM" src="https://github.com/user-attachments/assets/da935fd4-3778-4ed1-b3f3-07c1cce4be86" />

</p>
<p>
Second, I created a virtual machine to work as a client. I named it "client-1." It would connect to dc-1's domain and allow users to log into the domain from it. I performed this step while dc-1 was being created.
</p>
<br />

<p>
<img width="1370" alt="Screenshot 2024-12-18 at 8 39 57 PM" src="https://github.com/user-attachments/assets/b57865f8-20fe-4c85-a9df-e48e782a81f5" />

</p>
<p>
That is why this step is third and not second. I set the IP address to static. Normally, it is dynamic and the IP address would change whenever I shut the computer down. However, because it was to be used as a domain controller, I set it to static. That way, the client can use the IP address to find the server.
</p>
<br />

<p>
<img width="818" alt="Screenshot 2024-12-18 at 8 50 08 PM" src="https://github.com/user-attachments/assets/58b13be3-0ea6-4a02-a6e2-41a53b8f9f5a" />

</p>
<p>
And speaking of which, I set location of the DNS Server of client-1 to be the IP address of dc-1. That way, the client will use the domain controller as a DNS Server.
</p>
<br />

<p>
<img width="449" alt="Screenshot 2024-12-18 at 9 06 31 PM" src="https://github.com/user-attachments/assets/fb775b16-775e-4e6b-aee4-eb7b570c8bc1" />


</p>
<p>
After doing that, from client-1, I pinged dc-1 (the domain controller) to make sure they were on the same network.
</p>
<br />

<p>
<img width="684" alt="Screenshot 2024-12-18 at 9 06 57 PM" src="https://github.com/user-attachments/assets/3a97673b-fb57-4c1c-abeb-dcd71a9659e7" />


</p>
<p>
Then I used ipconfig /all to confirm that the DNS Server was registered as dc-1's IP address. The first time I tried this, I saw another random IP address. Then I remembered to go to Azure and restart the client-1 virtual machine. Once that was done, the DNS Server settings were set.
</p>
<br />

<p>
<img width="861" alt="Screenshot 2024-12-18 at 9 16 31 PM" src="https://github.com/user-attachments/assets/dfcb3a53-ab1f-44c5-9b74-5474b7224c77" />


</p>
<p>
Now, in order to use dc-1 as a server and data center, I had to activate the AD DS tools.
</p>
<br />

<p>
<img width="1012" alt="Screenshot 2024-12-18 at 10 37 50 PM" src="https://github.com/user-attachments/assets/bcf04e4c-d35c-4ba4-a799-9ec27ed69dd2" />


</p>
<p>
With my domain fully created, I went into client-1 and added it to the domain.
</p>
<br />

<p>
<img width="863" alt="Screenshot 2024-12-18 at 11 17 32 PM" src="https://github.com/user-attachments/assets/13f60a12-b13a-4a30-b648-949c2a7c78fd" />


</p>
<p>
Then, I set permissions for the clients on my domain. Determining how many failed log ins they can have before they are locked out. And for how long they are locked out. I also know how to grant access to one who is locked out and how to reset passwords. But I did not show that here.
</p>
<br />
