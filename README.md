# Help Desk — Network Setup and Troubleshooting Home Lab

## About This Repository

Help desk work in the real world is never one thing. A single shift can involve
installing an operating system on a new laptop, resetting a locked account,
chasing down a printer that nobody can print to, explaining to a user why their
mailbox is full, removing a piece of malware, and walking someone through a
reboot they've already tried three times. The job is part networking, part
systems administration, part security, part customer service and the people
who are good at it are the ones who have broken enough things to recognize the
pattern when it breaks again.

This repository is my attempt to build that experience deliberately. Everything
here runs in a home lab, on virtual machines, with snapshots taken before every
risky change. That means I can break things on purpose, misconfigure DNS, lock
myself out of a domain, corrupt a boot record, hand a client a duplicate IP
address, and then actually fix them, instead of reading about someone else
doing it.

The repository is organised as a series of **projects**. Each project covers one
area of help desk work, lives in its own folder, and includes its own
screenshots, notes, and configuration files. I update it roughly **once a week**,
so expect the repo to grow steadily rather than arrive finished.

---

## Project 01 — Network Setup and Troubleshooting *(current)*

**This is the focus of the repository right now.** Everything below describes
Project 01. Later projects are listed in the roadmap further down and will
each get their own folder and documentation as they are completed.

### Objectives

- Install operating systems and configure their settings
- Set up a virtual network switch in VMware Workstation to replicate real-world network topologies
- Configure a firewall
- Connect clients to the firewall
- Set up a DNS server
- Configure the default gateway
- Assign static IP addresses
- Configure the network

### Overview

The initial goal of this project was to practice basic networking terms and
concepts in a home lab, without the fear of breaking anything or being unable to
recover from an incident. The project is separated into different parts, and each
week I will update the repository. I will try to emphasize core concepts and
important tips for performing this lab in the most professional way, so that not
only help desk enthusiasts will learn, but also have the opportunity to
experiment, break things, and expand their knowledge of the networking side of
this field.

The lab is built on VMware Workstation. The virtual switch lets me carve out
segments that behave like the ones I'd meet in a real office — a client VLAN
behind a firewall, a server segment, an isolated test segment — so that when I
misconfigure a route or point a client at the wrong DNS server, the failure looks
the same as it would on real hardware. And because it's virtual, a snapshot
restores the whole thing in under a minute.

---

## Repository Structure

Each project gets its own folder, with its own documentation and screenshots.
Nothing is shared between projects except the top-level README.

├── README.md
├── LICENSE
├── .gitignore
└── projects/
├── 01-network-setup/
│ ├── README.md # detailed walkthrough for this project
│ ├── screenshots/ # step-by-step evidence
│ └── configs/ # exported configs, notes, commands
├── 02-windows-basics/
├── 03-active-directory/
└── ... # added as each project is completed


The top-level README (this file) is the index. The per-project README is the
actual walkthrough — commands run, problems hit, how they were fixed, and what
I would do differently next time.

---

## Roadmap

The topics below are the areas of help desk work I intend to cover. The order is
a sequence, not a priority list — each project builds on the one before it, which
is why networking comes first.

| # | Project | What it covers | Status |
|---|---|---|---|
| 01 | Network Setup and Troubleshooting | VMware virtual switches, firewall, DNS, static IPs, gateways, client connectivity | **In progress** |
| 02 | Windows Basics and Operating System Environments | OS installation, drivers, updates, user profiles, local accounts, boot troubleshooting | Planned |
| 03 | Active Directory and User Management | Domain setup, OUs, groups, password resets, account lockouts, GPOs, permissions | Planned |
| 04 | Microsoft 365 | Licensing, mailbox management, Teams, MFA, password resets, common admin tasks | Planned |
| 05 | Printers | Drivers, print queues, network printers, spooler issues, permissions | Planned |
| 06 | Antivirus and Endpoint Protection | Microsoft Defender, scans, quarantine, exclusions, false positives | Planned |
| 07 | File Shares and Permissions | NTFS vs share permissions, access troubleshooting, inheritance | Planned |
| 08 | Software Installation and Deployment | Silent installs, packaging, version conflicts, rollback | Planned |
| 09 | Remote Support | RDP, remote assistance, VPN access, supporting a user who isn't in front of you | Planned |
| 10 | Backup and Recovery | Image backups, restore testing, recovering a broken system | Planned |
| 11 | Ticket Triage and Documentation | Writing up an incident so the next person can follow it | Planned |

The list will change as I go — some projects will split, some will merge, and
some will turn out to be less useful than I expected. That's part of the point.

---

## What This Repository Does Not Cover

**Hardware troubleshooting.** You may ask why. The reason is simple: there are
other resources that cover this topic in far greater detail and in a much more
professional way than I could. Faulty RAM, dead motherboards, failing drives, and
physical diagnostics need real hardware, real tools, and hands-on practice — none
of which a virtual lab can give you. Pointing you at better material is more
useful than a shallow imitation of it.

---

## Lab Philosophy

Three rules I follow in every project here:

1. **Snapshot before you break it.** Every risky change starts from a known-good
   snapshot. If the fix takes longer than the restore, restore.
2. **Break it on purpose.** Reading that a duplicate IP causes an address
   conflict is not the same as watching two machines fight over one address and
   then finding it in the logs. Deliberate failure is the fastest teacher.
3. **Write it down.** If I can't explain a fix in a way that someone else could
   follow, I didn't understand it well enough. That's what these folders are for.

---

## Updates

I update this repository roughly once a week. Each update adds screenshots,
configuration files, and notes to the relevant project folder, and the roadmap
table above is updated to match. If something has been sitting at "Planned" for
a long time, feel free to open an issue and ask about it.

---

## License

Released under the MIT License. See [`LICENSE`](LICENSE).