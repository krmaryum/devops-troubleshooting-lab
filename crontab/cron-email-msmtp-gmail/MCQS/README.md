# Cron Email with Gmail SMTP using msmtp MCQ Quiz — README

## Overview

This HTML file contains a **25-question multiple-choice quiz** about configuring **cron email notifications** using **Gmail SMTP** and **msmtp**.

It is designed to help practice the full setup flow, important commands, common errors, and real-world troubleshooting steps.

## Main File

| File | Description |
|---|---|
| `cron-email-msmtp-gmail-25-mcq-quiz.html` | Interactive 25-question MCQ quiz with shuffled answers, timer, score, answer checking, and short explanations |

## Features

- 25 multiple-choice questions
- Shuffled correct answers
- Answer checking
- Score calculation
- 20-minute timer
- Correct and wrong answer highlighting
- Short explanation for each question
- Reset quiz option
- Mobile-friendly design

## Topics Covered

- What `msmtp` is
- Why cron needs SMTP configuration
- What `MAILTO` does
- Gmail App Password vs normal Gmail password
- Google 2-Step Verification requirement
- `/etc/msmtprc`
- `~/.msmtprc`
- Securing SMTP credentials
- Creating `/var/log/msmtp.log`
- Testing `msmtp` directly
- Testing the `mail` command
- Testing cron email with `MAILTO`
- Understanding output redirection
- Using `MAILTO=""`
- Checking `/usr/sbin/sendmail`
- Common errors and fixes
- Stopping every-minute cron test jobs

## How to Use

1. Download the HTML file.
2. Open it in any web browser.
3. Select your answers.
4. Click **Check Answers**.
5. Review your score and explanations.
6. Click **Reset Quiz** to practice again.

## Practice Commands

```bash
sudo apt update
sudo apt install msmtp msmtp-mta mailutils -y

sudo vim /etc/msmtprc
sudo chmod 600 /etc/msmtprc
sudo chown root:root /etc/msmtprc

sudo touch /var/log/msmtp.log
sudo chmod 666 /var/log/msmtp.log

printf "Subject: msmtp direct test\n\nTest email from Linux msmtp\n" | msmtp your-email@gmail.com

echo "Hello from mail command" | mail -s "Mail Test" your-email@gmail.com

crontab -e
```

## Cron Email Test

```cron
MAILTO="your-email@gmail.com"

* * * * * echo "Hello from cron at $(date)"
```

After testing, stop the every-minute job:

```cron
# * * * * * echo "Hello from cron at $(date)"
```

## Important Troubleshooting Commands

```bash
cat /var/log/msmtp.log
which msmtp
which mail
ls -l /usr/sbin/sendmail
readlink -f /usr/sbin/sendmail
systemctl status cron
grep CRON /var/log/syslog
```

## Security Reminder

Do not use your normal Gmail password.

Use a **Google App Password** only.

```text
Normal Gmail password = Do not use
Gmail App Password = Use for msmtp
```

Never share your Gmail App Password publicly or in screenshots.

## Best For

This quiz is useful for:

- Linux beginners
- DevOps students
- System Administrator practice
- SRE troubleshooting practice
- Cron automation labs
- RHCSA/RHEL-style learning
- Real-world email alert setup
- Interview revision

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
