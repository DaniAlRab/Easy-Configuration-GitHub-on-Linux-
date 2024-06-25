# Easy-Configuration-GitHub-on-Linux

To connect your GitHub account to a Linux terminal using Git, you need to set up SSH keys and configure Git. Here’s a step-by-step guide:

### Step 1: Install Git
First, ensure Git is installed on your system. You can check if Git is installed and install it if it isn't.

```bash
git --version
```

If Git is not installed, you can install it using the package manager for your Linux distribution.

**For Debian-based systems (e.g., Ubuntu):**

```bash
sudo apt update
sudo apt install git
```

**For Red Hat-based systems (e.g., Fedora, CentOS):**

```
bash
sudo dnf install git
```

### Step 2: Configure Git
Set your global Git username and email. This is necessary for commit messages.

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### Step 3: Generate SSH Key
Generate a new SSH key if you don't already have one.

```bash
ssh-keygen -t rsa -b 4096 -C "your.email@example.com"
```

When prompted, press Enter to save the key to the default location (`~/.ssh/id_rsa`) and enter a passphrase if you wish.

### Step 4: Add SSH Key to SSH Agent
Start the SSH agent and add your SSH key.

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```

### Step 5: Add SSH Key to GitHub
Copy the SSH key to your clipboard.

```bash
cat ~/.ssh/id_rsa.pub
```

Go to your GitHub account, navigate to **Settings** > **SSH and GPG keys**, and click **New SSH key**. Give your key a title and paste the key into the "Key" field.

### Step 6: Test SSH Connection
Test the SSH connection to GitHub.

```bash
ssh -T git@github.com
```

You should see a message like:

```
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

### Step 7: Clone a Repository
Now you can clone repositories using SSH.

```bash
git clone git@github.com:username/repository.git
```

### Additional Configuration
For repositories you already have cloned using HTTPS, you can switch to SSH.

```bash
cd path/to/your/repo
git remote set-url origin git@github.com:username/repository.git
```

With these steps, you have connected your GitHub account to your Linux terminal using Git and SSH, allowing you to interact with your repositories securely and efficiently.
