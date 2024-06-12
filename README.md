# File permissions in Linux
## Project description:
The research team at my organization needs to update the file permissions for specific files and directories within the projects directory. Currently, the permissions do not align with the required level of authorization. Ensuring these permissions are accurate will enhance system security. To achieve this, I completed the following tasks:

### Check File and Directory Details

The following code demonstrates how I used Linux commands to identify the existing permissions for a specific directory in the file system:
<p align="center">
<img src="https://i.imgur.com/AjqCdMf.png" height="80%" width="80%" alt="LinuxPermissions"/>

The first line in the screenshot shows the command I entered, and the subsequent lines display the output. The code lists all contents of the projects directory. I used the 'ls -la' command to produce a detailed listing of the file contents, including hidden files. The output indicates one directory named drafts, one hidden file named .project_x.txt, and five other project files. The 10-character string in the first column represents the permissions set on each file or directory.

### Describe the Permissions String

The 10-character string can be broken down to determine who is authorized to access the file and their specific permissions. The characters and their meanings are as follows:

- 1st character: Indicates the file type (d for directory, - for regular file).
- 2nd-4th characters: Indicate read (r), write (w), and execute (x) permissions for the user. A hyphen (-) means the permission is not granted.
- 5th-7th characters: Indicate read (r), write (w), and execute (x) permissions for the group. A hyphen (-) means the permission is not granted.
- 8th-10th characters: Indicate read (r), write (w), and execute (x) permissions for others. A hyphen (-) means the permission is not granted.

For example, the file permissions for project_t.txt are -rw-rw-r--. The hyphen (-) indicates that project_t.txt is a file. The second, fifth, and eighth characters are all r, meaning user, group, and others have read permissions. The third and sixth characters are w, indicating only the user and group have write permissions. No one has execute permissions for project_t.txt.

### Change File Permissions

The organization decided that others shouldn't have write access to any files. Based on the previously returned file permissions, I identified that project_k.txt must have write access removed for others.

The following code demonstrates how I used Linux commands to accomplish this:
<p align="center">
<img src="https://i.imgur.com/XVktWBl.png" height="80%" width="80%" alt="LinuxPermissions"/>

The first two lines of the screenshot show the commands I entered, and the remaining lines display the output of the second command. The 'chmod' command changes file and directory permissions. The first argument specifies the permissions to be changed, and the second argument indicates the file or directory. In this example, I removed write permissions from others for the project_k.txt file. After this, I used 'ls -la' to verify the updates.

### Change File Permissions on a Hidden File

The research team recently archived project_x.txt and wants no one to have write access, but the user and group should have read access.

The following code demonstrates how I used Linux commands to change the permissions:
<p align="center">
<img src="https://i.imgur.com/w51Xpfm.png" height="80%" width="80%" alt="LinuxPermissions"/>

The first two lines of the screenshot show the commands I entered, and the remaining lines display the output of the second command. .project_x.txt is a hidden file, indicated by the period (.) at the beginning of its name. In this example, I removed write permissions from the user and group and added read permissions to the group. I removed write permissions from the user with 'u-w', then removed write permissions from the group with g-w, and added read permissions to the group with 'g+r'.

### Change Directory Permissions

The organization wants only the researcher2 user to have access to the drafts directory and its contents, meaning no one else should have execute permissions.

The following code demonstrates how I used Linux commands to change the permissions:
<p align="center">
<img src="https://i.imgur.com/w51Xpfm.png" height="80%" width="80%" alt="LinuxPermissions"/>

The output displays the permission listing for several files and directories. Line 1 indicates the current directory (projects), and line 2 indicates the parent directory (home). Line 3 is a regular file named .project_x.txt. Line 4 is the drafts directory with restricted permissions. Only researcher2 has execute permissions. Previously, the group had execute permissions, which I removed using the 'chmod' command. Researcher2 already had execute permissions, so no additional changes were needed.

## Summary

I adjusted multiple permissions to match the desired authorization levels for files and directories in the projects directory. First, I used 'ls -la' to check the current permissions, informing my subsequent steps. Then, I used the chmod command multiple times to update the permissions on various files and directories accordingly.
