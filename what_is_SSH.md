# What is SSH?

### What is SSH? What is it used for?
SSH, also known as Secure Shell or Secure Socket Shell, is a network protocol that gives users, particularly system administrators, a secure way to access a computer over an unsecured network.

SSH also refers to the suite of utilities that implement the SSH protocol. Secure Shell provides strong password authentication and public key authentication, as well as encrypted data communications between two computers connecting over an open network, such as the internet.

In addition to providing strong encryption, SSH is widely used by network administrators to manage systems and applications remotely, enabling them to log in to another computer over a network, execute commands and move files from one computer to another.

<br>

### How does SSH work? 
Secure Shell was created to replace insecure terminal emulation or login programs, such as Telnet, rlogin (remote login) and rsh (remote shell). SSH enables the same functions -- logging in to and running terminal sessions on remote systems. SSH also replaces file transfer programs, such as File Transfer Protocol (FTP) and rcp (remote copy).
The most basic use of SSH is to connect to a remote host for a terminal session. The form of that command is the following:

`ssh UserName@SSHserver.example.com`

This command will cause the client to attempt to connect to the server named server.example.com, using the user ID UserName. If this is the first time negotiating a connection between the local host and the server, the user will be prompted with the remote host's public key fingerprint and prompted to connect, despite there having been no prior connection:

```
The authenticity of host 'sample.ssh.com' cannot be established.

 DSA key fingerprint is 01:23:45:67:89:ab:cd:ef:ff:fe:dc:ba:98:76:54:32:10.
 Are you sure you want to continue connecting (yes/no)?
 ```

Answering yes to the prompt will cause the session to continue, and the host key is stored in the local system's known_hosts file. This is a hidden file, stored by default in a hidden directory, called /.ssh/known_hosts, in the user's home directory. Once the host key has been stored in the known_hosts file, the client system can connect directly to that server again without need for any approvals; the host key authenticates the connection.

<br>

### What are Private and Public keys?
The motivation for using public key authentication over simple passwords is security. Public key authentication provides cryptographic strength that even extremely long passwords can not offer. With SSH, public key authentication improves security considerably as it frees the users from remembering complicated passwords (or worse yet, writing them down).

In addition to security public key authentication also offers usability benefits - it allows users to implement single sign-on across the SSH servers they connect to. Public key authentication also allows automated, passwordless login that is a key enabler for the countless secure automation processes that execute within enterprise networks globally.

In the SSH public key authentication use case, it is rather typical that the users create (i.e. provision) the key pair for themselves. SSH implementations include easily usable utilities for this (for more information see ssh-keygen and ssh-copy-id).

Each SSH key pair includes two keys:

1. A public key that is copied to the SSH server(s). Anyone with a copy of the public key can encrypt data which can then only be read by the person who holds the corresponding private key. Once an SSH server receives a public key from a user and considers the key trustworthy, the server marks the key as authorized in its authorized_keys file. Such keys are called authorized keys.

2. A private key that remains (only) with the user. The possession of this key is proof of the user's identity. Only a user in possession of a private key that corresponds to the public key at the server will be able to authenticate successfully. The private keys need to be stored and handled carefully, and no copies of the private key should be distributed. The private keys used for user authentication are called identity keys.

<br>

### Why use SSH? How does it increase security?
Nefarious computer users have a variety of tools at their disposal enabling them to disrupt, intercept, and re-route network traffic in an effort to gain access to a system. In general terms, these threats can be categorized as follows:

Interception of communication between two systems — In this scenario, the attacker can be somewhere on the network between the communicating parties, copying any information passed between them. The attacker may intercept and keep the information, or alter the information and send it on to the intended recipient.

This attack can be mounted through the use of a packet sniffer — a common network utility.

Impersonation of a particular host — Using this strategy, an attacker's system is configured to pose as the intended recipient of a transmission. If this strategy works, the user's system remains unaware that it is communicating with the wrong host.

This attack can be mounted through techniques known as DNS poisoning or IP spoofing.

Both techniques intercept potentially sensitive information and, if the interception is made for hostile reasons, the results can be disastrous.

If SSH is used for remote shell login and file copying, these security threats can be greatly diminished. This is because the SSH client and server use digital signatures to verify their identity. Additionally, all communication between the client and server systems is encrypted. Attempts to spoof the identity of either side of a communication does not work, since each packet is encrypted using a key known only by the local and remote systems.

<br>

### How can you create an SSH key pair?
After you've checked for existing SSH keys, you can generate a new SSH key to use for authentication, then add it to the ssh-agent.

1. Open Git Bash.
2. Paste the text below, substituting in your GitHub email address. 

```ssh-keygen -t ed25519 -C "your_email@example.com"```

-> This creates a new SSH key, using the provided email as a label. It will print out:

```> Generating public/private ALGORITHM key pair.```

3. When you're prompted to "Enter a file in which to save the key", you can press Enter to accept the default file location.

`> Enter a file in which to save the key (/c/Users/YOU/.ssh/id_ALGORITHM):[Press enter]`

4. At the prompt, type a secure passphrase. 
```
> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again] 
```

<br>

Sources:
- [What is SSH and how does it work? - techtarget.com](https://www.techtarget.com/searchsecurity/definition/Secure-Shell)
- [Public and Private Keys - ssh.com](https://www.ssh.com/academy/ssh/public-key-authentication#:~:text=Private%20key%20stays%20with%20the,have%20the%20corresponding%20private%20key.)
- [Why use SSH? - vskills.in](https://www.vskills.in/certification/certified-linux-administrator-ssh)
- [Generating a new SSH key - docs.github.com](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)