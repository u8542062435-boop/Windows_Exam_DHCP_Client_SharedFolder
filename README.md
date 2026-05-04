# Windows Server — DHCP, Client & Shared Folder

> Configuring the DHCP role, connecting a client to the domain, and setting up a shared folder with permissions.

---

## Table of Contents

1. [DHCP Role Installation](#1-dhcp-role-installation)
2. [Scope Options](#2-scope-options)
3. [Client Network Configuration](#3-client-network-configuration)
4. [Joining the Domain](#4-joining-the-domain)
5. [Creating the Shared Folder](#5-creating-the-shared-folder)
6. [Accessing the Shared Folder from the Client](#6-accessing-the-shared-folder-from-the-client)

---

## 1. DHCP Role Installation

Install the **DHCP Server** role and create a new scope to define the IP range that will be assigned to clients.

![DHCP Role Installation](https://github.com/user-attachments/assets/ab33722a-059d-4c74-bb28-5b2bcb5e279f)

![New Scope](https://github.com/user-attachments/assets/f307ed29-33d5-44bc-ba59-8baf98147937)

---

## 2. Scope Options

Configure the scope options that clients will receive alongside their IP address.

**Default Gateway (Router)**

![Default Gateway](https://github.com/user-attachments/assets/c2798d07-09bf-4736-91c6-9afb43681c13)

**DNS Server** — so clients can resolve domain names.

![DNS Server](https://github.com/user-attachments/assets/1aec2cff-b3cc-4808-a971-42d73ebfa5d1)

Finally, **activate the scope** and **authorize the DHCP server** in Active Directory.

![Activate & Authorize](https://github.com/user-attachments/assets/7662dcbe-80e6-4ff8-9f95-c028b10d4bac)

---

## 3. Client Network Configuration

On the **client machine**, open Network Adapter settings and set it to obtain an IP address automatically via DHCP.

![DHCP Client Settings](https://github.com/user-attachments/assets/a273d80c-b7de-4d1b-bb00-fe46e278f06e)

Run `ipconfig /release` followed by `ipconfig /renew` to force the client to request a new IP from the DHCP server.

![ipconfig renew](https://github.com/user-attachments/assets/298cbbbf-3888-4c3c-b4d3-cc910e2166b6)

Verify the lease on the server side under **DHCP Manager → Address Leases**.

![Address Leases](https://github.com/user-attachments/assets/6b39c363-8a54-4084-96a5-bb23d91b7bdc)

---

## 4. Joining the Domain

On the client, go to **System Properties → Computer Name → Change** and enter the domain name.

![Domain Join](https://github.com/user-attachments/assets/d1aac060-0ad0-426c-aae2-e8734997b79f)

Authenticate with a domain admin account and restart the client to apply the changes.

![Domain Authentication](https://github.com/user-attachments/assets/3c770a53-aa03-4362-958c-75dd5108e4fc)

---

## 5. Creating the Shared Folder

On the **server**, create the folder to be shared, configure the **sharing permissions**, and define who can access it.

![Sharing Permissions](https://github.com/user-attachments/assets/172ab3bc-beea-4f21-aa55-af6bac948e7f)

Also configure the **NTFS permissions** to control access at the file system level.

![NTFS Permissions](https://github.com/user-attachments/assets/93c8db33-fba0-416b-91dc-5d1be5be88fc)

---

## 6. Accessing the Shared Folder from the Client

From the **client**, access the shared folder using its UNC path: `\\ServerName\ShareName`

![UNC Path Access](https://github.com/user-attachments/assets/291757bd-353a-4904-a891-f10b78508930)

Verify that the client can read and write according to the permissions configured.

![Permission Verification](https://github.com/user-attachments/assets/52d431e2-2ffc-43e7-8e53-d20d8b2a924a)

> The client cannot create folders — this is expected behavior based on the permission settings defined in Step 5.

---

