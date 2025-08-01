# Linux System Monitoring

## Introduction to System Monitoring
Monitoring system resources is essential to ensure optimal performance, detect issues, and troubleshoot problems in Linux. Various tools allow us to monitor CPU, memory, disk usage, network activity, and running processes.

## Index of Commands Covered

### CPU and Memory Monitoring
- `top` – Real-time system monitoring whereas ps aux shows lists of running processes but not realtime process listing.
- `htop` – Interactive process viewer (requires installation)
- `vmstat` – Report system performance statistics
  <img width="799" height="142" alt="Screenshot 2025-08-02 at 9 32 41 AM" src="https://github.com/user-attachments/assets/08777034-10dc-4818-82ec-ec001f67c781" />
- `free -m` – Show memory usage in machine readable format
- `free -h` - Show memory usage in human readable format
- `nproc` = amount of CPU available
 <img width="707" height="172" alt="Screenshot 2025-08-02 at 9 36 44 AM" src="https://github.com/user-attachments/assets/94f609f8-443a-4394-9cc8-5a91db83a77c" />

**top command shows interactive realtime monitoring hence cannot be used in Shell scripts as it doesn't give static output. So if you're running any shell script, use vmstat or free -m command which gives static o/p**

### Disk Monitoring
- `df -h` – Check disk space usage
- `du -sh /path` – Show disk usage of a specific directory
- `du -sh` - suppose you're in any folder and now wants to see disk spaces of it then run du -sh command.
 <img width="331" height="192" alt="Screenshot 2025-08-02 at 9 44 33 AM" src="https://github.com/user-attachments/assets/7fc6e1ee-95cf-4741-b0fe-1c23da749ae2" />

- `iostat` – Display CPU and disk I/O statistics

### Network Monitoring
- `ifconfig` – Show network interfaces (deprecated, use `ip a`)
- `ip a` – Show network interface details
- `netstat -tulnp` – Show active connections and listening ports
- `ss -tulnp` – Alternative to `netstat` for socket statistics
- `ping hostname` – Test network connectivity
- `traceroute hostname` – Show network path to a host
- `nslookup domain` – Get DNS resolution details

### Log Monitoring
- `tail -f /var/log/syslog` – Live monitoring of system logs
- `journalctl -f` – Live system logs for systemd-based distros
- `dmesg | tail` – View kernel logs

## CPU and Memory Monitoring
### Using `top`
To view real-time CPU and memory usage:
```bash
top
```
Press `q` to quit.

### Using `htop`
A user-friendly alternative:
```bash
htop
```
Use arrow keys to navigate and `F9` to kill processes.

### Using `vmstat`
To check CPU, memory, and I/O stats:
```bash
vmstat 1 5  # Update every 1 sec, show 5 updates
```

### Checking Memory Usage
```bash
free -m
```
Shows free and used memory in megabytes.

## Disk Monitoring
### Using `df`
Check available disk space:
```bash
df -h
```
### Using `du`
Find the size of a directory:
```bash
du -sh /var/log
```
### Using `iostat`
Check disk and CPU usage:
```bash
iostat
```

## Network Monitoring
### Checking Network Interfaces
```bash
ip a  # Show IP addresses and interfaces
```
### Viewing Open Ports and Connections
```bash
netstat -tulnp  # Show listening ports
ss -tulnp  # Alternative to netstat
```
### Testing Connectivity
```bash
ping google.com  # Test internet connection
traceroute google.com  # Trace the path to Google
```
### Checking DNS Resolution
```bash
nslookup example.com
```

## Log Monitoring
### Live Monitoring of System Logs
```bash
tail -f /var/log/syslog  # Follow logs in real-time
journalctl -f  # Systemd logs
```
### Checking Kernel Logs
```bash
dmesg | tail
```
