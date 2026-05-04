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
<img width="527" height="318" alt="imatge" src="https://github.com/user-attachments/assets/298cbbbf-3888-4c3c-b4d3-cc910e2166b6" />

<br>
We can verify the lease on the server side in the DHCP Manager under **Address Leases** <br>
<br>
<img width="667" height="132" alt="imatge" src="https://github.com/user-attachments/assets/6b39c363-8a54-4084-96a5-bb23d91b7bdc" />


---

## Step 4 <br>
<br>
Now we join the **client to the domain**. We go to System Properties > Computer Name > Change and enter the domain name <br>
<br>
<img width="317" height="287" alt="imatge" src="https://github.com/user-attachments/assets/d1aac060-0ad0-426c-aae2-e8734997b79f" />

<br>
We authenticate with a domain admin account and restart the client <br>
<br>
<img width="569" height="527" alt="imatge" src="https://github.com/user-attachments/assets/3c770a53-aa03-4362-958c-75dd5108e4fc" />


---

## Step 5 <br>
<br>
On the **server**, we create the folder that will be shared. We set the sharing permissions and define who can access it <br>
<br>
<img width="366" height="395" alt="imatge" src="https://github.com/user-attachments/assets/172ab3bc-beea-4f21-aa55-af6bac948e7f" />
 <br>
<br>
We also configure the **NTFS permissions** to control access at the file system level <br>
<br>
<img width="390" height="496" alt="imatge" src="https://github.com/user-attachments/assets/93c8db33-fba0-416b-91dc-5d1be5be88fc" />
<br>

---

## Step 6 <br>
<br>
From the **client**, we access the shared folder using its UNC path: `\\ServerName\ShareName` <br>
<br>
<img width="566" height="280" alt="imatge" src="https://github.com/user-attachments/assets/291757bd-353a-4904-a891-f10b78508930" />
 <br>
<br>
We verify that the client can read/write depending on the permissions set <br>
<br>
<img width="598" height="380" alt="imatge" src="https://github.com/user-attachments/assets/52d431e2-2ffc-43e7-8e53-d20d8b2a924a" />
<br>
The client can't create a folder because the permission settings are fixed to this.

