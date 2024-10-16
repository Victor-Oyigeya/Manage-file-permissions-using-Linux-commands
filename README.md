# Manage file permissions using Linux commands

## Environment/Labs used:
- <b>Linux</b>
- <b>Bash Shell</b>

## Project description
The research team at my organization needs to update the file permissions for certain files and directories within the projects directory. The permissions do not currently reflect the level of authorization that should be given. Checking and updating these permissions will help keep their system secure. To complete this task, I performed the following tasks:

## Open terminal
![Screenshot 2024-09-04 220816](https://github.com/user-attachments/assets/24699683-55bd-4cb9-a3c3-187a755c9308)

## Navigate to the projects directory
![Screenshot 2024-09-04 222443](https://github.com/user-attachments/assets/2d95d33e-7597-42bf-8f12-3525b3d06393)

## Check file and directory details
The following code demonstrates how I used Linux commands to determine the existing permissions set for a specific directory in the file system.

![Screenshot 2024-09-04 222910](https://github.com/user-attachments/assets/3a726a0e-7d10-4a08-9fa5-ca6d0e5ffe13)


The first line of the screenshot displays the command I entered, and the other lines display the output. The code lists all contents of the projects directory. I used the <b>ls</b> command with the <b>-la</b> option to display a detailed listing of the file contents that also returned hidden files. The output of my command indicates that there is one directory named drafts, one hidden file named .project_x.txt, and five other project files. The 10-character string in the first column represents the permissions set on each file or directory.

## Describe the permissions string
The 10-character string can be deconstructed to determine who is authorized to access the file and their specific permissions. The characters and what they represent are as follows:

-	<b>1st character: This character is either a d or hyphen (-) and indicates the file type. If it’s a d, it’s a directory. If it’s a hyphen (-), it’s a regular file.</b>
-	
-	<b>2nd-4th characters: These characters indicate the read (r), write (w), and execute (x) permissions for the user. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted to the user.</b>
-	
-	<b>5th-7th characters: These characters indicate the read (r), write (w), and execute (x) permissions for the group. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted for the group.</b>
-	
-	<b>8th-10th characters: These characters indicate the read (r), write (w), and execute (x) permissions for other. This owner type consists of all other users on the system apart from the user and the group. When one of these characters is a hyphen (-) instead, that indicates that this permission is not granted for other.</b>

For example, the file permissions for <b>project_t.txt</b> are <b>-rw-rw-r--</b>. Since the first character is a hyphen (-), this indicates that <b>project_t.txt</b> is a file, not a directory. The second, fifth, and eighth characters are all <b>r</b>, which indicates that <b>user</b>, <b>group</b>, and <b<other</b> all have read permissions. The third and sixth characters are <b>w</b>, which indicates that only the <b>user</b> and <b>group</b> have write permissions. No one has execute permissions for <b>project_t.txt</b>.

## Change file permissions
The organization determined that <b>other</b> shouldn't have write access to any of their files. To comply with this, I referred to the file permissions that I previously returned. I determined <b>project_k.txt</b> must have the write access removed for <b>other</b>.

The following code demonstrates how I used Linux commands to do this:

 ![Screenshot 2024-09-04 223437](https://github.com/user-attachments/assets/4c0c67a2-68ea-40b1-8c61-f8c70382c29d)


The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. The <b>chmod</b> command changes the permissions on files and directories. The first argument indicates what permissions should be changed, and the second argument specifies the file or directory. In this example, I removed write permissions from <b>other</b> for the <b>project_k.txt</b> file. After this, I used <b>ls -la</b> to review the updates I made.

## Change file permissions on a hidden file
The research team at my organization recently archived <b>.project_x.txt</b>. They do not want anyone to have write access to this project, but the <b>user</b> and <b>group</b> should have read access. 

The following code demonstrates how I used Linux commands to change the permissions:

 ![Screenshot 2024-09-04 225942](https://github.com/user-attachments/assets/231ddd21-3a0d-4cb6-9adc-f0cf6841bbc6)


The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. I know .<b>project_x.txt</b> is a hidden file because it starts with a period (.). In this example, I removed write permissions from the <b>user</b> and <b>group</b>, and added read permissions to the <b>group</b>. I removed write permissions from the <b>user</b> with <b>"u-w"</b>. Then, I removed write permissions from the <b>group</b> with <b>"g-w"</b>, and added read permissions to the <b>group</b> with <b>"g+r"</b>. 

## Change directory permissions
My organization only wants the <b>researcher2 user</b> to have access to the drafts directory and its contents. This means that no one other than <b>researcher2</b> should have execute permissions.

The following code demonstrates how I used Linux commands to change the permissions:

 ![Screenshot 2024-09-04 230330](https://github.com/user-attachments/assets/e4b8874b-2bba-4951-942f-ab2526c7a4b2)


The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. I previously determined that the <b>group</b> had execute permissions, so I used the <b>chmod</b> command to remove them. The <b>researcher2 user</b> already had execute permissions, so they did not need to be added.

## Summary
I changed multiple permissions to match the level of authorization my organization wanted for files and directories in the projects directory. The first step in this was using <b>ls -la</b> to check the permissions for the directory. This informed my decisions in the following steps. I then used the <b>chmod</b> command multiple times to change the permissions on files and directories.


