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
<img width="371" height="395" alt="imatge" src="https://github.com/user-attachments/assets/c2798d07-09bf-4736-91c6-9afb43681c13" />
<br>
We also set the **DNS Server** so clients can resolve domain names <br>
<br>
<img width="388" height="400" alt="imatge" src="https://github.com/user-attachments/assets/1aec2cff-b3cc-4808-a971-42d73ebfa5d1" />
<br>
Finally, we **activate the scope** and **authorize the DHCP server** in Active Directory <br>
<br>
<img width="443" height="249" alt="imatge" src="https://github.com/user-attachments/assets/7662dcbe-80e6-4ff8-9f95-c028b10d4bac" />


---

## Step 3 <br>
<br>
Now we configure the **client machine**. We open Network Adapter settings and set it to obtain an IP address automatically (DHCP) <br>
<br>
<img width="402" height="445" alt="imatge" src="https://github.com/user-attachments/assets/a273d80c-b7de-4d1b-bb00-fe46e278f06e" />

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
