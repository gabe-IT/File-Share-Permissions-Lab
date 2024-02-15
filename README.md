# File Share Permissions Lab

## Create Sample File Shares with Various Permissions

1. **Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)**:
   - Open Remote Desktop Connection or use Azure Portal to connect to DC-1.
   - Log in using the credentials for the domain admin account.

2. **Connect/log into Client-1 as a normal user (mydomain\<someuser>)**:
   - Open Remote Desktop Connection or use Azure Portal to connect to Client-1.
   - Log in using the credentials for the normal user account (<someuser>).

3. **Create Folders on DC-1**:
   - On DC-1, navigate to the C:\ drive.
   - Create the following folders: “read-access”, “write-access”, “no-access”, “accounting”.
     - Right-click on the C:\ drive -> New -> Folder.
     - Repeat the process to create each folder.

4. **Set Permissions for the Folders**:
   - Right-click on each folder and select "Properties".
   - Go to the "Sharing" tab and click on "Advanced Sharing".
   - Check the box for "Share this folder".
   - Click on "Permissions" and add the "Domain Users" group.
     - For "read-access" folder, assign "Read" permission to the "Domain Users" group.
     - For "write-access" folder, assign "Read" and "Write" permissions to the "Domain Users" group.
     - For "no-access" folder, assign "Read" and "Write" permissions to the "Domain Admins" group.

5. **Attempt to Access File Shares as a Normal User**:
   - On Client-1, open File Explorer.
   - In the address bar, type `\\dc-1` and press Enter.
   - Try to access each of the shared folders.
   - Note down which folders you can access and which folders you cannot.

## Create an “ACCOUNTANTS” Security Group, Assign Permissions, and Test Access

1. **Create the “ACCOUNTANTS” Security Group**:
   - Return to DC-1.
   - Open Active Directory Users and Computers.
   - Right-click on the domain and select "New" -> "Group".
   - Name the group as “ACCOUNTANTS” and click "OK".

2. **Assign Permissions to the “ACCOUNTANTS” Group**:
   - Right-click on the “accounting” folder on DC-1.
   - Go to "Properties" -> "Security" tab -> "Edit" -> "Add".
   - Add the “ACCOUNTANTS” group and grant it "Read/Write" permissions.
   - Click "Apply" and then "OK" to save the changes.

3. **Test Access as <someuser>**:
   - Log out of Client-1 as <someuser>.
   - Log back into DC-1.
   - Add <someuser> to the “ACCOUNTANTS” Security Group.
     - Open Active Directory Users and Computers.
     - Find <someuser> and add them to the “ACCOUNTANTS” group.
   - Log back into Client-1 as <someuser>.
   - Try to access the “accounting” share in `\\DC-1`. 

4. **Verify Access**:
   - Check if <someuser> can now access the “accounting” folder on DC-1.
   - Ensure that <someuser> can read from and write to the folder as expected.

## Conclusion

Congratulations! You have successfully completed the File Share Permissions Lab. 
You have created sample file shares with various permissions and tested access for different user groups.
