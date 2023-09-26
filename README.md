## Steps for establishing a secure SSH repository

### 1. Creating Local Repository
```
git init
git add .
git status
git commit -m "your comment"
```
![AltText](/Images/creating_local_repo.png)

<br>

### 2. Creating GitHub Repo
![AltText](/Images/creating_github_repo.png)

<br>

### 3. Creating .ssh Folder
![AltText](/Images/create_ssh_folder.png)

<br>

### 4. Opening .ssh Folder
![AltText](Images/opening_ssh_folder.png)

<br>

### 5. Generating public/private key pair
```
ssh-keygen -t rsa -b 4096 -C "your email"
```
![AltText](Images/generating_public_private_key_pair.png)

- `-t rs` => encription (other option: *dsa*)
- `-b 4096` => bit length
- `-C` => comment at the end of the key

<br>

### 6. Get the public key
![AltText](Images/getting_public_key.png)

<br>

### 7. Adding SSH to GitHub Repository
![AltText](Images/adding_ssh_to_github.png)
![AltText](Images/ssh_on_github.png)

<br>

### 8. Giving the key to the agent
![AltText](Images/giving_the_key_to_the_agent.png)

<br>

### 9. Verifying the successful creation of the SSH connection

![AltText](Images/successful_auth.png)

<br>

### 10. Final step
![AltText](Images/add_origin.png)
![AltText](Images/adding_ssh.png)
