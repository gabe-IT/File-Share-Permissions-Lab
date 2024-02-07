# File Share Permissions Lab

## Create Sample File Shares with Various Permissions

1. Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin).

2. Connect/log into Client-1 as a normal user (mydomain\<someuser>).

3. On DC-1, on the C:\ drive, create 4 folders: “read-access”, “write-access”, “no-access”, “accounting”.

4. Set the following permissions (share the folder) for the “Domain Users” group:
   - Folder: “read-access”, Group: “Domain Users”, Permission: “Read”.
   - Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write”.
   - Folder: “no-access”, Group: “Domain Admins”, Permissions: “Read/Write”.

5. Attempt to access file shares as a normal user:
   - On Client-1, navigate to the shared folder (start, run, \\dc-1).
   - Try to access the folders you just created. 
   - Note which folders you can access and which folders you can create stuff in.

## Create an “ACCOUNTANTS” Security Group, Assign Permissions, and Test Access

1. Go back to DC-1, in Active Directory, create a security group called “ACCOUNTANTS”.

2. On the “accounting” folder you created earlier, set the following permissions:
   - Folder: “accounting”, Group: “ACCOUNTANTS”, Permissions: “Read/Write”.

3. On Client-1, as <someuser>, try to access the accountants folder. It should fail. 

4. Log out of Client-1 as <someuser>.

5. On DC-1, make <someuser> a member of the “ACCOUNTANTS” Security Group.

6. Sign back into Client-1 as <someuser> and try to access the “accounting” share in \\DC-1\. Does it work now?

