## Rails Academy: Lesson 101

In this less we will cover all the fundamental command line tricks you'll need for this course.

This lesson is **required** for all other lessons.

### Topics

1. [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) 
2. [GitHub](https://github.com)
3. [GitHub CLI (gh)](https://cli.github.com)

### Register your Skool account

1. Visit [Skool](https://skool.com) your profile (top right)
2. Copy your "Skool ID" and paste it into the terminal when prompted
3. Run: 
 
```bash
ra skool @skool-username
```

### Change directory into the lesson folder

```bash
cd ~/ralessons/ra-101
```

### Generate an SSH key

```bash
ssh-keygen -t ed25519
```

Press enter to accept the all the defaults, and select **do not enter a password**

### GitHub

#### Signup to Github

1. Visit [GitHub](https://github.com)
2. Create an account (or login if you already have one)

#### Copy your public key

On Mac run:

```
pbcopy < ~/.ssh/id_ed25519.pub
```

On Ubuntu and Windows run:

```
cat ~/.ssh/id_ed25519.pub
```

Copy the output of that command.

#### Paste your public key into GitHub

3. Choose "Settings" -> "SSH and GPG keys" -> "New SSH Key"

3. In 1Password find "GitHub SSH Key" and copy the **public key**
4. Paste your public key into the "Key" field
5. Click "Add SSH Key"

Test your SSH key by running the following in Alacritty:

```bash
ssh -T git@github.com
```

If that worked you should see:

```
Hi yourgithubusername! You've successfully authenticated, but GitHub does not provide shell access.
```

### Change a file

Lets make a small change that we can check into Git.

```bash
ra details > ra_details.log
```

Now lets add this change to git with a message:

```bash
git add ra_details.log
```

And commit that change to our local repository

```bash
git commit -m "Added a log file for review"
```

### Create a branch

Make sure you are in the `~/ralessons/ra-101` directory

```bash
cp ~/ralessons/ra-101
```

Create a git branch with your Skool name like so:

```bash
git branch $RA_SKOOL
git checkout $RA_SKOOL
```

In Alacritty you should see this before every command:

```
~/ralessons/ra-101 [@skool-username]
$ _
```

This means git is currently on the `@skool-username` branch.

### Create a Pull Request

Lets get GitHub CLI interface connected, run:

```bash
gh auth login
```

Choose `Github.com -> HTTPS -> Login with web browser`

#### Create your first PR

After logging in run:

```bash
gh pr create
```

1. Select the default branch `ra-101[@your-skool-username]`
2. Set a `Title` to `Please review my first lesson` (or anything you like)
3. Submit

If you've completed everything you should see a url like:

```
https://github.com/justintanner/ra-101/pull/1
```

### :tada: You made to the end.

Check back at the URL above if there is any feedback from your teacher, otherwise move on the next lesson.

#### [Lesson 102](https://github.com/justintanner/ra-102)

### Resources

1. :youtube: [Bash in 100 Seconds](https://www.youtube.com/watch?v=I4EWvMFj37g)
