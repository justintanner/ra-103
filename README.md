## Rails Academy: Lesson 101 - Command Line Essentials

This lesson covers the basic command line tricks we'll need to do lessons on Rails Academy.

If you don't understand all the commands, don't worry! We'll be using them a lot in the future, so you'll get plenty of practice.

### Topics

- Bash 
- GitHub
- SSH Keys
- GitHub CLI (gh)

### Prerequisites

[Install Rails Academy](http://rails.academy)

### 1. Sign Up for GitHub

Visit [GitHub](https://github.com) and create a **free** account or log in if you already have one.

### 2. Generate a local SSH Key

Open Alacritty and run the following command:

```bash
ssh-keygen -t ed25519
```

- Press Enter multiple times to accept to all the defaults
- Do *not enter* a passphrase when prompted

### 3. Copy your SSH Key

#### macOS

```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

#### Ubuntu and Windows

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the text that is outputted.

### 4. Add your SSH Key to GitHub

- In GitHub, navigate to Settings > SSH and GPG keys > New SSH Key
- Paste your public key into the “Key” field
- Select a title for the key like "Rails Academy Key"
- Click "Add SSH Key"

### 5. Test that GitHub is connected

```bash
ssh -T git@github.com
```

Expected output:

```bash
Hi yourgithubusername! You've successfully authenticated, but GitHub does not provide shell access.
```

### 6. Create a Branch

First, let's make sure we are in the right folder.

```bash
cd ~/ralessons/ra-101
```

Then we'll need to:

- Visit [Skool](https://skool.com) and copy your “Skool ID” from your profile
- Create a branch with your Skool username with the command below:

```bash
git branch @my-skool-username
git checkout @my-skool-username
```

Your terminal prompt should now show:

```bash
~/ralessons/ra-101 [@my-skool-username]
$ _
```

This means git is currently on the `@skool-username` branch.

### 7. Add a File to Git

```bash
echo "@my-skool-username" > skool.txt
git add skool.txt
git commit -m "Added skool.txt with my Skool ID"
```

Lets double check the log, to make sure the commit was successful:

```bash
git log
```

Your should see something like:

```bash
commit 1234567890abcdef1234567890abcdef12345678 (HEAD -> @my-skool-username)
Author: yourgithubusername <yourgithubemail>
Date:   Mon Jan 1 00:00:00 2021 -0500

    Added skool.txt with my Skool ID
```

### 8. Create a Pull Request

- Authenticate with GitHub CLI:

```bash
gh auth login
```

* Select GitHub.com > HTTPS > Login with web browser.
* Create the PR:

```bash
gh pr create
```

* Press Enter multiple times to accept the defaults
* Select Submit
* You should get a link to your PR, it should look like this:

```bash
https://github.com/yourusername/ra-101/pull/1
```

* Visit your PR on Github.

The automatic check will run if your code passes, you'll see:

:white_check_mark: All checks have passed

### :tada: You're Done! :tada:

#### Additional Resources

- :tv: [How to clone, push, and pull with git](https://www.youtube.com/watch?v=yxvqLBHZfXk)
- :tv: [Bash in 100 Seconds](https://www.youtube.com/watch?v=I4EWvMFj37g)
- :tv: [Git Explained in 100 Seconds](https://www.youtube.com/watch?v=hwP7WQkmECE)



