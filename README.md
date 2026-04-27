# Windows_Exam_DHCP_Client_SharedFolder

## Step 1 <br>
<br>
On our first block of tasks we must install and configure DHCP rol for the server <br>
<br>
<img width="540" height="449" alt="imagen" src="https://github.com/user-attachments/assets/ab33722a-059d-4c74-bb28-5b2bcb5e279f" /> <br>
<br>
We add a new scope <br>
<br>
<img width="496" height="447" alt="imatge" src="https://github.com/user-attachments/assets/f307ed29-33d5-44bc-ba59-8baf98147937" />

---

## Step 2 <br>
<br>
We configure the scope options: set the **Default Gateway (Router)** that the clients will receive <br>
<br>
[screenshot — Scope Options > 003 Router, entering the gateway IP] <br>
<br>
We also set the **DNS Server** so clients can resolve domain names <br>
<br>
[screenshot — Scope Options > 006 DNS Servers, entering the DNS IP] <br>
<br>
Finally, we **activate the scope** and **authorize the DHCP server** in Active Directory <br>
<br>
[screenshot — Right-click on server > Authorize / Activate Scope]

---

## Step 3 <br>
<br>
Now we configure the **client machine**. We open Network Adapter settings and set it to obtain an IP address automatically (DHCP) <br>
<br>
[screenshot — Network Adapter Properties > IPv4 > Obtain an IP address automatically] <br>
<br>
We run `ipconfig /release` and `ipconfig /renew` to force the client to request an IP from our DHCP server <br>
<br>
[screenshot — CMD showing ipconfig with the leased IP from our scope] <br>
<br>
We can verify the lease on the server side in the DHCP Manager under **Address Leases** <br>
<br>
[screenshot — DHCP Manager > Scope > Address Leases showing the client]

---

## Step 4 <br>
<br>
Now we join the **client to the domain**. We go to System Properties > Computer Name > Change and enter the domain name <br>
<br>
[screenshot — System Properties > Domain join dialog] <br>
<br>
We authenticate with a domain admin account and restart the client <br>
<br>
[screenshot — Credentials prompt / restart confirmation]

---

## Step 5 <br>
<br>
On the **server**, we create the folder that will be shared. We set the sharing permissions and define who can access it <br>
<br>
[screenshot — Folder Properties > Sharing tab > Advanced Sharing] <br>
<br>
We also configure the **NTFS permissions** to control access at the file system level <br>
<br>
[screenshot — Security tab > Edit permissions, adding users/groups]

---

## Step 6 <br>
<br>
From the **client**, we access the shared folder using its UNC path: `\\ServerName\ShareName` <br>
<br>
[screenshot — File Explorer with the UNC path in the address bar] <br>
<br>
We verify that the client can read/write depending on the permissions set <br>
<br>
[screenshot — Shared folder contents visible from the client]
