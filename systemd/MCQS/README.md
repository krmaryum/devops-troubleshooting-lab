# systemd MCQ Quiz — README

## Overview

This HTML file contains a **25-question multiple-choice quiz** about **systemd in Linux**.

It is designed for Linux, DevOps, System Administrator, and RHCSA-style practice.

## Main File

| File | Description |
|---|---|
| `systemd-25-mcq-quiz.html` | Interactive systemd quiz with 25 MCQs |

## Features

- 25 multiple-choice questions
- Answer checking
- Score calculation
- 20-minute timer
- Correct and wrong answer highlighting
- Short explanation for each question
- Reset quiz option
- Mobile-friendly design

## Topics Covered

- What is systemd?
- systemd as PID 1
- `systemctl` commands
- Start vs enable
- Service states
- Unit files
- `.service`, `.target`, and `.timer`
- `journalctl` logs
- Custom service files
- Targets
- Troubleshooting failed services

## How to Use

1. Download the HTML file.
2. Open it in any web browser.
3. Select answers for all questions.
4. Click **Check Answers**.
5. Review your score and explanations.
6. Click **Reset Quiz** to practice again.

## Best For

This quiz is useful for:

- Linux beginners
- DevOps students
- System Administrator practice
- RHCSA/RHEL preparation
- Interview revision
- Classroom or self-study practice

## Study Tip

After completing the quiz, practice these commands in your Linux lab:

```bash
ps -p 1
systemctl status nginx
systemctl is-active nginx
systemctl is-enabled nginx
journalctl -u nginx -n 50
systemctl get-default
```

## Quick Summary

This quiz helps reinforce the most important systemd concepts:

- `systemd` manages Linux services.
- `systemctl` controls services and units.
- `journalctl` reads logs.
- `enable` means start at boot.
- `start` means run now.
- `daemon-reload` is needed after editing unit files.
