# OverTheWire Bandit — Linux & Cybersecurity Practice

![Linux](https://img.shields.io/badge/Linux-Command%20Line-FCC624?logo=linux&logoColor=black)
![OverTheWire](https://img.shields.io/badge/OverTheWire-Bandit-222222)
![Levels](https://img.shields.io/badge/Levels-0--33-blue)

A practical walkthrough of the **OverTheWire Bandit** wargame, documenting the Linux commands, concepts, and problem-solving techniques used from Level 0 through Level 33.

The focus is not on storing passwords, but on understanding **how each challenge was solved and why the commands work**.

> **Security note:** Passwords, private SSH keys, and other credentials are intentionally excluded from this repository.

---

## What I Practiced

- Linux navigation and file handling
- File permissions and ownership
- Searching and filtering files
- Standard input/output and redirection
- Pipes and command chaining
- Text processing and transformation
- Base64, ROT13, and hexadecimal data
- File identification and compression
- SSH and SSH key authentication
- Network services and port scanning
- Cron jobs and scheduled tasks
- Setuid programs
- Git repositories, branches, tags, and history
- Restricted-shell escape concepts
- Command-line troubleshooting

---

# Level-by-Level Walkthrough

## Level 0 → Level 1 — First SSH Login

**What I did:** Connected to the Bandit server over SSH and inspected the home directory.

**Key commands:** `ssh`, `ls`, `cat`

**What I learned:** How SSH access works and how to locate and read a basic file from the Linux terminal.

---

## Level 1 → Level 2 — Reading a File Named `-`

**What I did:** Read a file whose name is a single dash.

**Key command:** `cat ./-`

**What I learned:** `-` has a special meaning to many command-line programs, so adding `./` makes it clear that it is a filename.

---

## Level 2 → Level 3 — Filename With Spaces

**What I did:** Accessed a file whose name contains spaces.

**Key technique:** Quoting the filename.

**What I learned:** The shell normally separates arguments at spaces, so filenames containing spaces need quoting or escaping.

---

## Level 3 → Level 4 — Hidden Files

**What I did:** Listed hidden files inside a directory and identified the required file.

**Key command:** `ls -la`

**What I learned:** Linux filenames beginning with `.` are hidden from a normal `ls` listing.

---

## Level 4 → Level 5 — Identifying the Correct File

**What I did:** Inspected several files and determined which one contained readable text.

**Key commands:** `file`, `cat`

**What I learned:** File extensions are not always reliable; `file` can inspect the actual file type.

---

## Level 5 → Level 6 — Searching by File Properties

**What I did:** Searched a directory tree for a file matching specific size and permission requirements.

**Key command:** `find`

**What I learned:** `find` can filter files by type, size, permissions, ownership, and other attributes.

---

## Level 6 → Level 7 — Searching the Whole Filesystem

**What I did:** Searched from the filesystem root for a file matching a particular owner, group, and size.

**Key command:** `find / ... 2>/dev/null`

**What I learned:** The difference between searching from `.` and `/`, and how `2>/dev/null` hides permission-denied error messages.

---

## Level 7 → Level 8 — Searching File Contents

**What I did:** Used `grep` to find a specific piece of information inside a large file.

**Key command:** `grep`

**What I learned:** `grep` searches the contents of files rather than their filenames.

---

## Level 8 → Level 9 — Finding Unique Data

**What I did:** Processed repeated lines to identify the line that appeared only once.

**Key commands:** `sort`, `uniq`

**What I learned:** `uniq` works on adjacent duplicate lines, so sorting the data first can make it useful for finding unique entries.

---

## Level 9 → Level 10 — Extracting Readable Text

**What I did:** Extracted human-readable strings from a binary-looking file.

**Key command:** `strings`

**What I learned:** Binary files can contain readable text that can sometimes be extracted without opening the file as normal text.

---

## Level 10 → Level 11 — Base64 Decoding

**What I did:** Decoded data that had been encoded using Base64.

**Key command:** `base64 -d`

**What I learned:** Base64 is an encoding format, not encryption, and can be reversed with the appropriate decoder.

---

## Level 11 → Level 12 — ROT13 Transformation

**What I did:** Reversed a ROT13 transformation applied to alphabetic characters.

**Key command:** `tr 'A-Za-z' 'N-ZA-Mn-za-m'`

**What I learned:** `tr` can perform character-by-character substitutions, making it useful for simple text transformations such as ROT13.

---

## Level 12 → Level 13 — Hexdump and Layered Compression

**What I did:** Reconstructed binary data from a hexdump and repeatedly identified and extracted compressed/archive layers.

**Key tools:** `xxd`, `file`, `gzip`, `gunzip`, `bzip2`, `bunzip2`, `tar`

**What I learned:** A file can contain several layers of different formats. The reliable approach is to identify the current format with `file`, then use the matching tool before checking the next layer.

---

## Level 13 → Level 14 — SSH Private Key

**What I did:** Located the supplied `sshkey.private` file and learned how to use an SSH private key for authentication.

**Key commands:** `chmod 600`, `ssh -i`

**What I learned:** SSH private keys require restrictive permissions and can authenticate a user without typing that user's password directly.

---

## Level 14 → Level 15 — Netcat and a Local Service

**What I did:** Sent the current credential to a service listening on a local TCP port.

**Key tool:** `nc`

**What I learned:** Netcat can create simple network connections and send data to a listening service.

---

## Level 15 → Level 16 — SSL/TLS Connection

**What I did:** Connected to a local service that required an encrypted SSL/TLS connection.

**Key tool:** `openssl s_client`

**What I learned:** Network services may require different protocols; `openssl s_client` can establish and test TLS connections from the command line.

---

## Level 16 → Level 17 — Port Scanning

**What I did:** Scanned a range of local ports, identified the relevant service, and tested the candidate ports using TLS.

**Key tools:** `nmap`, `openssl s_client`

**What I learned:** Port scanning can be used to discover available services, after which individual services can be investigated more closely.

---

## Level 17 → Level 18 — Comparing Files

**What I did:** Compared two almost-identical files and identified the changed line.

**Key command:** `diff`

**What I learned:** `diff` is useful for finding changes between files, configurations, and versions of data.

---

## Level 18 → Level 19 — SSH With a Remote Command

**What I did:** Ran a command directly through SSH instead of starting an interactive shell.

**Key technique:** `ssh user@host "command"`

**What I learned:** SSH can execute a single remote command without opening a normal interactive session.

---

## Level 19 → Level 20 — Setuid Binary

**What I did:** Inspected and used a setuid program available in the home directory.

**Key concept:** `setuid`

**What I learned:** A setuid executable can run with the permissions of its owner, making file permissions especially important for system security.

---

## Level 20 → Level 21 — Netcat Listener and Setuid

**What I did:** Set up a listening network connection and used the supplied program to communicate with it.

**Key tool:** `nc`

**What I learned:** A program can connect to a listener on a chosen port, allowing two terminal sessions to exchange data.

---

## Level 21 → Level 22 — Cron Jobs

**What I did:** Inspected the system's scheduled tasks and traced a cron job to the script it executed.

**Key concepts:** `cron`, `/etc/cron.d/`

**What I learned:** Scheduled jobs can run automatically under specific users, so understanding their scripts and permissions is important when investigating a Linux system.

---

## Level 22 → Level 23 — Understanding Script Logic

**What I did:** Read the cron script and reproduced the command it used to calculate an output filename.

**Key tools:** `md5sum`, `cut`

**What I learned:** Reading a script carefully can reveal how it generates paths and processes data, allowing the same logic to be followed manually.

---

## Level 23 → Level 24 — Cron and Shell Scripts

**What I did:** Examined a cron-controlled directory and created a script that would be processed by the scheduled job.

**Key concepts:** Shell scripting, `cron`, file permissions

**What I learned:** Writable scheduled-job directories can create serious security problems when scripts are executed with another user's privileges.

---

## Level 24 → Level 25 — Small-Range Brute Force

**What I did:** Generated possible four-digit combinations and sent them to a network service along with the required credential.

**Key tools:** `for`, `seq`, `nc`

**What I learned:** A small search space can be systematically enumerated with shell scripting and piped into another program.

---

## Level 25 → Level 26 — Restricted Login and Pager Escape

**What I did:** Worked with a restricted login environment and used the pager/editor interaction to reach a normal shell.

**Key concepts:** Restricted shells, `more`, `vi`/`vim`

**What I learned:** Security restrictions can depend on the programs launched by a shell, and full-featured programs may provide their own escape mechanisms.

---

## Level 26 → Level 27 — Setuid After a Shell Escape

**What I did:** Continued from the restricted environment and used the resulting shell access with the available setuid program.

**Key concepts:** `setuid`, shell escape

**What I learned:** Permissions and execution context matter as much as the command itself when investigating privileged programs.

---

## Level 27 → Level 28 — Git Clone

**What I did:** Cloned a Git repository available on the local system and inspected its contents.

**Key command:** `git clone`

**What I learned:** Important information can exist inside source-code repositories, so Git repositories should be inspected as part of file and configuration investigations.

---

## Level 28 → Level 29 — Git History

**What I did:** Inspected the repository's commit history to find information that had previously been present.

**Key command:** `git log`

**What I learned:** Removing a secret from the latest version of a repository does not necessarily remove it from Git history.

---

## Level 29 → Level 30 — Git Branches

**What I did:** Examined the available branches and inspected a branch containing information that was not present in the default branch.

**Key commands:** `git branch -a`, `git checkout`

**What I learned:** Different branches can contain different versions of files and may hold information that is absent from the main working tree.

---

## Level 30 → Level 31 — Git Tags

**What I did:** Inspected the repository's tags and examined the relevant Git object.

**Key commands:** `git tag`, `git show`

**What I learned:** Tags are Git objects and can contain useful metadata or messages beyond the contents of normal tracked files.

---

## Level 31 → Level 32 — Git Push and `.gitignore`

**What I did:** Worked with a repository that required a particular file and content to be pushed to the remote repository. A `.gitignore` rule had to be handled explicitly.

**Key commands:** `git add -f`, `git commit`, `git push`

**What I learned:** `.gitignore` prevents normal tracking but is not a security mechanism; files can be explicitly forced into Git when appropriate.

---

## Level 32 → Level 33 — Restricted Uppercase Shell

**What I did:** Investigated a shell that transformed normal commands into uppercase and used a shell variable to escape the restriction.

**Key concept:** `$0`

**What I learned:** Shell variables and the distinction between a wrapper program and the underlying shell can be important when dealing with restricted command environments.

---

# Main Commands and Concepts

| Area | Examples |
|---|---|
| Navigation | `pwd`, `ls`, `cd`, `cat` |
| Search | `find`, `grep` |
| Inspection | `file`, `strings`, `diff` |
| Text processing | `sort`, `uniq`, `tr`, `cut` |
| Encoding | `base64`, `xxd`, ROT13 |
| Compression | `gzip`, `gunzip`, `bzip2`, `bunzip2` |
| Archives | `tar` |
| Permissions | `chmod`, ownership, setuid |
| Networking | `nc`, `nmap`, `openssl s_client` |
| Remote access | `ssh`, `scp` |
| Scheduling | `cron` |
| Version control | `git clone`, `git log`, `git branch`, `git tag`, `git push` |
| Shell concepts | Pipes, redirection, variables, restricted shells |

---

# Security Practices

- Credentials are not stored in this repository.
- Private SSH keys are not committed to Git.
- Screenshots should be checked for exposed credentials before publication.
- Commands are documented for educational purposes rather than as a place to store secrets.

---

# Learning Outcome

Working through the levels provided practical experience with Linux administration, command-line investigation, basic networking, file permissions, shell scripting, scheduled jobs, Git, and introductory security concepts.

The biggest lesson was learning to **read the clues, identify the data format or system behavior, choose the appropriate tool, verify the result, and then move to the next stage**.

---

## Reference

- [OverTheWire Bandit](https://overthewire.org/wargames/bandit/)
