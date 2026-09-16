# OverTheWire Bandit — MENSEC Assignment 2

![Linux](https://img.shields.io/badge/Linux-Command%20Line-FCC624?logo=linux&logoColor=black)
![OverTheWire](https://img.shields.io/badge/OverTheWire-Bandit-222222)
![Status](https://img.shields.io/badge/Status-Completed-2ea44f)

## About

This repository documents my practical work for **MENSEC Consulting Assignment 2**, based on the **OverTheWire Bandit** wargame.

The assignment provided hands-on experience with Linux command-line operations and introductory cybersecurity concepts through a sequence of progressively challenging tasks.

## Assignment Objectives

The practical exercise focused on developing the ability to:

- Navigate the Linux filesystem and manage files and directories.
- Understand file permissions, ownership, and access control.
- Locate files using attributes such as size, owner, group, and permissions.
- Work with standard input, output, pipelines, and error redirection.
- Search, filter, decode, and transform text from the command line.
- Identify unknown file types using the `file` utility.
- Extract and process compressed files and archives.
- Work with SSH authentication and SSH private keys.
- Troubleshoot command-line errors systematically.
- Approach security-oriented problems through observation, clues, and command-line investigation.

## Progress

**Completed:** Bandit Levels **0–33**.

The challenges were approached sequentially, using the information provided by each level to determine the appropriate Linux command or technique for the next step.

> **Security note:** Passwords, private SSH keys, and other authentication credentials are intentionally excluded from this repository.

## Linux Commands & Utilities Practiced

| Category | Tools |
|---|---|
| Navigation & files | `pwd`, `ls`, `cd`, `cat` |
| Search & inspection | `find`, `grep`, `file`, `strings` |
| Text processing | `sort`, `uniq`, `tr` |
| Encoding & data | `base64`, `xxd`, `md5sum` |
| Compression & archives | `gzip`, `gunzip`, `bzip2`, `bunzip2`, `tar` |
| Permissions | `chmod` |
| Remote access | `ssh`, `scp` |
| Shell concepts | Pipes (`\|`), redirection (`>`), error redirection (`2>/dev/null`) |

## Key Concepts Demonstrated

### Linux Permissions

Understanding permission notation such as `600` and how read, write, and execute permissions are assigned to the owner, group, and other users.

### File Discovery

Using `find` with conditions such as file type, size, ownership, group, and executability to locate specific files.

### File Identification

Using `file` to determine the actual format of files whose extensions do not necessarily reveal their contents.

### Data Transformation

Using command-line utilities such as `base64`, `tr`, and `xxd` to decode or transform data according to the requirements of individual challenges.

### Compression & Archives

Working through different compression and archive formats, including gzip, bzip2, and tar, and selecting the appropriate extraction tool based on the identified format.

### SSH Authentication

Using SSH to access remote Linux environments and working with SSH private-key authentication where required.

## Security & Credential Handling

Credentials obtained during the exercises are **not stored in this repository**. Private keys and passwords should never be committed to a public GitHub repository.

Screenshots used as evidence should also be reviewed before publication to ensure that authentication secrets are not exposed.

## Learning Outcome

Completing the Bandit practical strengthened my understanding of Linux command-line workflows and introduced practical techniques used in cybersecurity environments, including:

- Linux filesystem navigation
- Permissions and ownership
- File discovery and analysis
- Text processing and pipelines
- Encoding and decoding
- Compression and archive handling
- SSH authentication
- Command-line troubleshooting
- Security-conscious handling of credentials

## Assignment Information

| Item | Details |
|---|---|
| Program | MENSEC Consulting |
| Assignment | 2 |
| Practical | OverTheWire Bandit |
| Challenge Range | Levels 0–33 |
| Platform | Linux / Kali Linux |
| Status | Completed |

## Repository Purpose

This repository serves as a concise record of the practical skills and techniques applied while completing the MENSEC Assignment 2 Bandit challenges.

**Completed as part of my MENSEC Consulting practical training.**
