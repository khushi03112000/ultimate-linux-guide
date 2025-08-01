# User Management in Linux

## Introduction to User Management in Linux
Linux is a multi-user operating system, meaning multiple users can operate on a system simultaneously. Proper user management ensures security, controlled access, and system integrity. 

**Command to adduser** -> **useradd < username >**
Now to check if user is created correctly, check in **vim /etc/passwd**   

<img width="826" height="770" alt="Screenshot 2025-08-01 at 11 48 33 AM" src="https://github.com/user-attachments/assets/4278bd26-1f28-49d1-b924-34f21985ad0e" />    
  
Now what is a user without password, so set the password -> **passwd < username >** and check the password using **cat /etc/shadow.**   
Also if a user forgets a password or if u want to decrypt the password shown in the /etc/shadow folder, it is impossible as the encryption is highly secure and one way only.

<img width="1409" height="776" alt="Screenshot 2025-08-01 at 11 49 22 AM" src="https://github.com/user-attachments/assets/a90698ac-7bbb-4300-a81b-a518a9cb4505" />

Key files involved in user management:
- `/etc/passwd` – Stores user account details.
- `/etc/shadow` – Stores encrypted user passwords.
- `/etc/group` – Stores group information.
- `/etc/gshadow` – Stores secure group details.

## Creating Users in Linux
To create a new user in Linux, use:

### `useradd` Command (For most Linux distributions)
```bash
useradd username
```
This creates a user without a home directory.

To create a user with a home directory:
```bash
useradd -m username
```

To specify a shell:
```bash
useradd -s /bin/bash username
```

### `adduser` Command (For Debian-based systems)
```bash
adduser username
```
This is an interactive command that asks for a password and additional details. Creates home directory as well for the user. Good command

### Normal users don't have admin rights to delete sbin folders and all, only Root user has  
Command to switch to diff user : **su - < username>**  
<img width="741" height="284" alt="Screenshot 2025-08-01 at 12 56 55 PM" src="https://github.com/user-attachments/assets/cdd5735c-1807-4a09-911e-6b61e43c8df8" />

## Managing User Passwords
To set or change a user’s password:
```bash
passwd username
```

### Enforcing Password Policies
- **Password expiration**: Set password expiry days
  ```bash
  chage -M 90 username
  ```
- **Lock a user account**
  ```bash
  passwd -l username
  ```
- **Unlock a user account**
  ```bash
  passwd -u username
  ```

## Modifying Users
Modify an existing user with `usermod`:
- Change the username:
  ```bash
  usermod -l new_username old_username
  ```
- Change the home directory:
  ```bash
  usermod -d /new/home/directory -m username
  ```
- Change the default shell:
  ```bash
  usermod -s /bin/zsh username
  ```

## Deleting Users
To remove a user but keep their home directory:
```bash
userdel username
```
To remove a user and their home directory:
```bash
userdel -r username
```

## Working with Groups
### Creating Groups
```bash
groupadd groupname
```

### Adding Users to Groups
```bash
usermod -aG groupname username
```

### Viewing Group Memberships
```bash
groups username
```

### Changing Primary Group
```bash
usermod -g new_primary_group username
```

## Sudo Access and Privilege Escalation
### Adding a User to Sudo Group
On Debian-based systems:
```bash
usermod -aG sudo username
```
On RHEL-based systems:
```bash
usermod -aG wheel username
```

### Granting Specific Commands with Sudo
Edit the sudoers file:
```bash
visudo
```
Then add:
```bash
username ALL=(ALL) NOPASSWD: /path/to/command
```
