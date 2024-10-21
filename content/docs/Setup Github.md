### **Check if you have an SSH key**

Run the following command to see if you already have an SSH key:

bash

Copy code

`ls -al ~/.ssh`

You should see something like `id_rsa` and `id_rsa.pub`. If these files are not present, you’ll need to generate a new SSH key.

### 2. **Generate a new SSH key (if you don't have one)**

If you don't have an SSH key, you can create one by running:

bash

Copy code

`ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`

Follow the prompts, and it will generate a key pair (`id_rsa` and `id_rsa.pub`) in the `~/.ssh` directory.

### 3. **Add your SSH key to the ssh-agent**

Run the following commands to start the `ssh-agent` and add your key:

bash

Copy code

`eval "$(ssh-agent -s)" ssh-add ~/.ssh/id_rsa`

### 4. **Add your SSH key to GitHub**

Now, you need to add the public key to your GitHub account:

- Copy the SSH key to your clipboard:
    
    bash
    
    Copy code
    
    `cat ~/.ssh/id_rsa.pub`
    
- Go to GitHub:
    
    - Navigate to **Settings** > **SSH and GPG keys**.
    - Click **New SSH Key** and paste your public key there.

### 5. **Test your SSH connection to GitHub**

To confirm that GitHub is now recognizing your SSH key, run:

bash

Copy code

`ssh -T git@github.com`

If successful, you'll see a message like:

vbnet

Copy code

`Hi your_username! You've successfully authenticated, but GitHub does not provide shell access.`

### 6. **Try pushing again**

Now, you can try pushing your changes again:

bash

Copy code

`git push origin main`

This should work without the permission error. Let me know if you encounter any other issues!