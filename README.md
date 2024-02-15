### Prerequisite labs:
https://github.com/gabe-IT/Azure-Domain-Controller-Setup

# File Share Permissions Lab

## Create Sample File Shares with Various Permissions

1. **Connect/log into DC-1 as your domain admin account (mydomain.com\a-gabe)**:
   - Open Remote Desktop Connection or use Azure Portal to connect to DC-1.
   - Log in using the credentials for the domain admin account.

2. **Connect/log into Client-1 as a normal user (mydomain\<someuser(use any example user that was created previously)>)**:
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
     - For "write-access" folder, assign "Read" and "Write" permissions to the "Domain Users" group.![Screenshot_1](https://github.com/gabe-IT/File-Share-Permissions-Lab/assets/148400020/daff6900-2f6b-44f5-8e15-849d9970bc59)

     - For "no-access" folder, assign "Read" and "Write" permissions to the "Domain Admins" group.![Screenshot_2](https://github.com/gabe-IT/File-Share-Permissions-Lab/assets/148400020/b0a07a3a-ac22-402a-97cd-0b4f5a5cd12f)


5. **Attempt to Access File Shares as a Normal User**:
   - On Client-1, open File Explorer.
   - In the address bar, type `\\dc-1` and press Enter.![Screenshot_4](https://github.com/gabe-IT/File-Share-Permissions-Lab/assets/148400020/bc0f02be-5cc5-4a0c-a2ab-4705444a34ee)

   - Try to access each of the shared folders.![Screenshot_7](https://github.com/gabe-IT/File-Share-Permissions-Lab/assets/148400020/934686f3-1188-45a3-8734-862a56030103)

   - Note down which folders you can access and which folders you cannot.![Screenshot_8](https://github.com/gabe-IT/File-Share-Permissions-Lab/assets/148400020/37ad7d49-66c6-4eee-881d-e7501452b699)
![Screenshot_9](https://github.com/gabe-IT/File-Share-Permissions-Lab/assets/148400020/f93dc87b-c56e-4e61-a17d-b37d5e569a59)


## Create an “ACCOUNTANTS” Security Group, Assign Permissions, and Test Access

1. **Create the “ACCOUNTANTS” Security Group**:
   - Return to DC-1.
   - Open Active Directory Users and Computers.
   - Right-click on the domain and select "New" -> "Group".![Screenshot_10](https://github.com/gabe-IT/File-Share-Permissions-Lab/assets/148400020/dd6c7b08-9320-4873-aae6-d38e7e28d223)

   - Name the group as “ACCOUNTANTS” and click "OK".
![Screenshot_11](https://github.com/gabe-IT/File-Share-Permissions-Lab/assets/148400020/11da927e-a749-4ad2-8f69-87b8a0973d91)

2. **Assign Permissions to the “ACCOUNTANTS” Group**:
   - Right-click on the “accounting” folder on DC-1.
   - Go to "Properties" -> "Security" tab -> "Edit" -> "Add".![Screenshot_12](https://github.com/gabe-IT/File-Share-Permissions-Lab/assets/148400020/72e0f211-4ae2-4265-bbd9-60ac3ea8ba67)

   - Add the “ACCOUNTANTS” group and grant it "Read/Write" permissions.
   - Click "Apply" and then "OK" to save the changes.

3. **Test Access as <someuser>**:
   - Log out of Client-1 as <someuser>.![Screenshot_15](https://github.com/gabe-IT/File-Share-Permissions-Lab/assets/148400020/1d4dee50-9b4f-4d67-8ffb-82ab711dedd5)

   - Log back into DC-1.
   - Add <someuser> to the “ACCOUNTANTS” Security Group.
     - Open Active Directory Users and Computers.![Screenshot_16](https://github.com/gabe-IT/File-Share-Permissions-Lab/assets/148400020/bde7f6c8-9235-4b09-92cb-2495bb25f111)

     - Find <someuser> and add them to the “ACCOUNTANTS” group.![Screenshot_17](https://github.com/gabe-IT/File-Share-Permissions-Lab/assets/148400020/fdb369df-77c1-4e3d-a22b-97d11b3b7733)

   - Log back into Client-1 as <someuser>.
   - Try to access the “accounting” share in `\\DC-1`. 

4. **Verify Access**:
   - Check if <someuser> can now access the “accounting” folder on DC-1.![Screenshot_21](https://github.com/gabe-IT/File-Share-Permissions-Lab/assets/148400020/9896aa6b-f52e-4434-ab9c-a19a4d11d5a1)

   - Ensure that <someuser> can read from and write to the folder as expected.

## Conclusion

Congratulations! You have successfully completed the File Share Permissions Lab. 
You have created sample file shares with various permissions and tested access for different user groups.
