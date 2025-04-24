---
deleted: true
tags: [cheatsheet]
title: SSH Command
created: '2025-04-20T13:44:43.531Z'
modified: '2025-04-24T19:03:32.302Z'
---

# SSH Command

In Linux, the ssh command is used to establish a secure, encrypted connection to a remote server, enabling remote access, file transfer, and command execution. 
Here's a breakdown of how to use the ssh command:
Basic Syntax:

    ssh [username@]hostname
        [username@] (optional): Specifies the username on the remote server. If omitted, the current user on the local machine is used.
        hostname: The IP address or domain name of the remote server. 

Examples:

    Connect as the current user: ssh 192.168.1.100
    Connect as a specific user: ssh user@192.168.1.100
    Connect using a domain name: ssh user@example.com 
    Overthewire: ssh bandit0@bandit.labs.overthewire.org -p 2220

Key Considerations:

    Security:
    SSH uses encryption to protect data transmitted between the client and server, making it a secure alternative to older protocols like Telnet. 

First-time connection:
When connecting to a new host for the first time, you might be prompted to confirm the authenticity of the host. Type "yes" and press Enter to proceed. 
Other SSH related commands:

    scp: Securely copy files between machines. 

sftp: Secure File Transfer Protocol, for interactive file transfers. 
ssh-keygen: Generate SSH key pairs for authentication. 
ssh-copy-id: Copy your public key to a remote server for passwordless login. 
ssh-agent: Manage SSH keys for authentication
