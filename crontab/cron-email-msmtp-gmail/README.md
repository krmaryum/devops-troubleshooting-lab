# Cron Email with Gmail SMTP using msmtp — README

## Overview

This study note explains how to configure **cron email notifications** on Linux using **Gmail SMTP** and **msmtp**.

It covers the full process from scratch, including setup, testing, errors, and fixes.

## Main File

| File | Description |
|---|---|
| `cron-email-msmtp-gmail-from-scratch-to-hero-study-notes.md` | Complete study notes for configuring cron email with Gmail SMTP using msmtp, including troubleshooting and fixes |

## What You Will Learn

- What cron email is
- What `MAILTO` does in crontab
- What `msmtp` is
- Why Linux needs SMTP configuration for external email
- How to create a Gmail App Password
- How to configure `/etc/msmtprc`
- How to test `msmtp` directly
- How to test the `mail` command
- How to test cron email using `MAILTO`
- How to stop test cron jobs
- How to redirect cron output to logs
- How to troubleshoot common errors

## Tools Used

- Linux cron/crontab
- Gmail SMTP
- Google App Password
- `msmtp`
- `mail` command
- `/etc/msmtprc`
- `/var/log/msmtp.log`

## Main Lab Flow

```text
1. Install msmtp and mailutils
2. Enable Gmail 2-Step Verification
3. Create Gmail App Password
4. Configure /etc/msmtprc
5. Secure /etc/msmtprc
6. Create /var/log/msmtp.log
7. Test msmtp directly
8. Test mail command
9. Test cron MAILTO
10. Stop the every-minute test job
```

## Important Commands

```bash
sudo apt update
sudo apt install msmtp msmtp-mta mailutils -y

sudo vim /etc/msmtprc
sudo chmod 600 /etc/msmtprc
sudo chown root:root /etc/msmtprc

sudo touch /var/log/msmtp.log
sudo chmod 666 /var/log/msmtp.log
```

## Email Test Commands

```bash
printf "Subject: msmtp direct test

Test email from Linux msmtp
" | msmtp your-email@gmail.com

echo "Hello from mail command" | mail -s "Mail Test" your-email@gmail.com
```

## Cron Test Example

```cron
MAILTO="your-email@gmail.com"

* * * * * echo "Hello from cron at $(date)"
```

After testing, stop the every-minute job:

```cron
# * * * * * echo "Hello from cron at $(date)"
```

## Common Error Covered

```text
mail: cannot send message: Process exited with a non-zero status
```

The notes explain how to fix this by checking:

```bash
cat /var/log/msmtp.log
which msmtp
which mail
ls -l /usr/sbin/sendmail
readlink -f /usr/sbin/sendmail
```

## Best For

This file is useful for:

- Linux beginners
- System Administrator practice
- DevOps students
- SRE troubleshooting practice
- Cron automation labs
- RHCSA/RHEL-style learning
- Real-world email alert setup

## Security Reminder

Do not use your normal Gmail password.

Use a **Google App Password** only.

```text
Normal Gmail password = Do not use
Gmail App Password = Use for msmtp
```

Never share your App Password publicly or in screenshots.

## Quick Summary

```text
cron = runs scheduled jobs
MAILTO = sends cron output to email
mail = command used to send email
msmtp = SMTP client that sends email through Gmail SMTP
Gmail App Password = special password for SMTP authentication
```

Golden rule:

```text
If cron output is not redirected, cron can email it.
If output is redirected to a log file, cron usually has nothing to email.
Use MAILTO="" when you want no email.
Use logs for production history.
Use email for alerts.
```
