## Rails Academy: Lesson 101

By the end of this lesson you will publish a "Hello World" app to real server.

### Topics

1. [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) 
2. [GitHub](https://github.com)
2. [GitHub CLI (gh)](https://cli.github.com)
3. [1Password](https://1password.com)
4. [Docker Hub](https://hub.docker.com)

### Verify your setup

1. Open Alacritty
2. Type the following command followed by Enter:

```bash
ra verify
```

**Note: If you don't have `ra` try [reinstalling Rails Academy](https://github.com/justintanner/rails-academy)**

### Register your Skool account

1. Visit [Skool](https://skool.com) your profile (top right)
2. Copy your "Skool ID" and paste it into the terminal when prompted
3. Run: 
 
```bash
ra skool @your-school-id
```

### Get into the lesson folder

```bash
cd ~/ralessons/ra-101
```

### 1Password (the hard way, best security)

1. Open 1Password from your Applications folder
2. Start a free trial (or login if you already have an account)
3. Select `1Password` from the menu bar and choose `Settings`
4. Navigate to the `Developer` tab and enable the following:

- :check: `Use the SSH agent`
- :check: `Integrate with 1Password CLI`

#### Generate an SSH Key with 1Password

1. Still in 1Password click "+ New Item"
2. Choose "SSH Key"
3. Enter the title "GitHub SSH Key"
4. Click "+ Add Private Key" -> "Generate a New Key"
5. Leave the default of "Ed25519" and click "Generate"
6. Click "Save"


### ssh-keygen (the easy way, but less secure)

If you don't want to use 1Password, we can create an SSH key manually.

1. Open Alacritty and type

```bash
ssh-keygen -t ed25519
```

2. Press enter to accept the all the defaults, and select no password

**Note: This will create a new SSH key on your computer only, if you lose it's on you.**

### GitHub

#### Signup to Github

1. Visit [GitHub](https://github.com)
2. Create an account (or login if you already have one)

#### Copy your public key from 1password

1. Open 1Password and find "GitHub SSH Key" created above
2. Copy the **public** key, not the private key.

#### Copy your public key from the "less secure way"

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
Hi yourname! You've successfully authenticated, but GitHub does not provide shell access.
```

### Docker Hub

We'll need a Docker Hub account to push and pull images.

1. Visit [Docker Hub](https://hub.docker.com)
2. Create an account (or login if you already have one)
3. Click your profile in the top right and choose "Account Settings"
4. Click "Security" and create a new access token
5. Open 1Password and create a new item with the title "Docker Hub Token"
6. Copy the token and paste it into the "Password" field
7. Click "Save"

### Your done! :tada:
