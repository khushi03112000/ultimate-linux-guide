# Understanding the Folder Structure

### Explanation of System Directories

### **Symbolic Links (Less Significant)**
| Directory | Description |
|-----------|-------------|
| `/sbin -> /usr/sbin` | System binaries(commands) for administrative commands (linked to `/usr/sbin`), hence grant sbin access to administrative users only|
| `/bin -> /usr/bin` | Essential user binaries(commands) (linked to `/usr/bin`), hence grant bin access to any user |
| `/lib -> /usr/lib` | Shared libraries and kernel modules (linked to `/usr/lib`). Used by Kernel mostly for making system calls with h/w to do actions|
<img width="591" height="319" alt="Screenshot 2025-07-31 at 6 50 14 PM" src="https://github.com/user-attachments/assets/d7fcf785-ec16-45be-a02a-ad66ff8f4b70" />


### **Important System Directories**
| Directory | Description |
|-----------|-------------|
| `/boot` | Stores files needed for booting(starting/restarting) the system i.e starting the linux machine (not relevant in containers coz they are stimulation of linux env). |
| `/usr` | Contains most user-installed applications and libraries. |
| `/var` | Stores logs, caches, and temporary files that change frequently. |
| `/etc` | Stores system configuration files. |

### **User & Application-Specific Directories**
| Directory | Description |
|-----------|-------------|
| `/home` | Default location for user home directories. |
| `/opt` | Used for installing optional third-party software like JAVA etc. You can install it anywhere in home directory or create any new directory but best practise says that to install 3rd party s/w use "opt" directory  |
| `/srv` | Holds data for services like web servers (rarely used in containers). |
| `/root` | Home directory for the root user. |

### **Temporary & Volatile Directories**
| Directory | Description |
|-----------|-------------|
| `/tmp` | Temporary files (cleared on reboot). |
| `/run` | Holds runtime data for processes. |
| `/proc` | Virtual filesystem for process and system information. |
| `/sys` | Virtual filesystem for hardware and kernel information. |
| `/dev` | Contains device files (e.g., `/dev/null`, `/dev/sda`). |

### **Mount Points**
| Directory | Description |
|-----------|-------------|
| `/mnt` | Temporary mount point for external filesystems. Folder used by linux administrators to mount new volumes(disks) |
| `/media` | Mount point for removable media (USB, CDs). |
| `/data` | Likely your **mounted volume** from Windows (`C:/ubuntu-data`). |
