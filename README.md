## Rails Academy: Lesson 101 - Command Line Essentials

In this course we are going to get **comfortable on the command-line**. This lesson will cover all the basic commands we'll need for all of the other lessons.

### Topics

- Bash 
- GitHub
- SSH Keys
- GitHub CLI (gh)

### 1. Register your Skool account

- Visit Skool and copy your “Skool ID” from your profile.
- In the terminal, run:
 
```bash
ra skool @skool-username
```

### 2. Navigate to the Lesson Folder

```bash
cd ~/ralessons/ra-101
```

### 3. Generate an SSH Key

```bash
ssh-keygen -t ed25519
```

- Press Enter to accept defaults.
- Do not enter a password when prompted.

### 4. Sign Up for GitHub

- Visit [GitHub](https://github.com) and create an account or log in if you already have one.

### 5. Add SSH Key to GitHub

#### macOS

```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

#### Ubuntu and Windows

```bash
cat ~/.ssh/id_ed25519.pub
```

- Copy the output.

### 6. Add SSH Key to GitHub

- In GitHub, navigate to Settings > SSH and GPG keys > New SSH Key.
- Paste your public key into the “Key” field.
- Click Add SSH Key.

### 7. Test SSH Connection

```bash
ssh -T git@github.com
```

Expected output:

```bash
Hi yourgithubusername! You've successfully authenticated, but GitHub does not provide shell access.
```

### 8. Add a File to Git

```bash
ra details > ra_details.log
git add ra_details.log
git commit -m "Added a log file for review"
```
### 9. Create a Branch

Make sure you are in the `~/ralessons/ra-101` directory

```bash
cp ~/ralessons/ra-101
```

- Create and switch to a branch named after your Skool username:

```bash
git branch @skool-username
git checkout @skool-username
```

Your terminal prompt should now show:

```bash
~/ralessons/ra-101 [@skool-username]
$ _
```

This means git is currently on the `@skool-username` branch.


### 10. Create a Pull Request

- Authenticate with GitHub CLI:

```bash
gh auth login
```

* Select GitHub.com > HTTPS > Login with web browser.
* Create the PR:

```bash
gh pr create
```

* Choose the default option (@skool-username -> main).
* Set the title to “Please review my first lesson”.
* Submit
* You’ll receive a URL like:

```bash
https://github.com/yourusername/ra-101/pull/1
```

### Completion

* Check the PR URL for any feedback from your teacher.
* Proceed to [Lesson 102](https://github.com/justintanner/ra-102) when ready.

### Resources

- :tv: [How to clone, push, and pull with git](https://www.youtube.com/watch?v=yxvqLBHZfXk)
- :tv: [Bash in 100 Seconds](https://www.youtube.com/watch?v=I4EWvMFj37g)
- :tv: [Git Explained in 100 Seconds](https://www.youtube.com/watch?v=hwP7WQkmECE)



