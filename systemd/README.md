# systemd — README

## Overview

This study note explains **systemd in Linux** using a simple learning flow:

- What is systemd?
- Why do we need systemd?
- How does systemd work?
- How to manage services using `systemctl`
- How to read logs using `journalctl`
- How to create a custom systemd service
- How to troubleshoot failed services

## Main File

| File | Description |
|---|---|
| `systemd-from-scratch-to-hero-study-notes.md` | Complete study notes for learning systemd from beginner to advanced level |

## Topics Covered

- Linux boot process overview
- systemd as PID 1
- Services and unit files
- `systemctl` commands
- Start vs enable
- Service states
- `journalctl` logs
- Custom `.service` file creation
- Targets and timers
- Troubleshooting flow
- Interview questions
- Command cheat sheet

## Best For

This note is useful for:

- Linux beginners
- DevOps students
- System Administrator practice
- RHCSA/RHEL preparation
- GitHub study repository documentation
- Interview revision

## Practice Recommendation

After reading the notes, practice these commands on Ubuntu or RHEL:

```bash
ps -p 1
systemctl status ssh
systemctl list-units
systemctl list-unit-files
journalctl -u ssh -n 50
systemctl get-default
```

For NGINX or Apache practice:

```bash
sudo systemctl status nginx
sudo systemctl status httpd
```

## Quick Summary

**systemd** is the main Linux service manager.  
**systemctl** controls services.  
**journalctl** reads service logs.  
`.service` files define how services start and stop.  
`.target` files represent system states.  
`.timer` files schedule tasks.
