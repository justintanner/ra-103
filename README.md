## Rails Academy: Lesson 103 - Deploying your first Rails application

In this lesson you will deploy rails to a real server.

You can use this *free server** for the other lessons or anything you want.

### Topics

- DockerHub
- Kamal

### Prerequisites

[Lesson 101](https://github.com/justintanner/ra-101)

### 1. Install the Rails Academy GitHub app

**If you have not [added your ssh keys](https://github.com/justintanner/ra-101?tab=readme-ov-file#2-generate-a-local-ssh-key) from [lesson 101](https://github.com/justintanner/ra-101) yet, please do so now.**

- Login to your [GitHub account](https://github.com)
- Install the [Rails Academy GitHub App](https://github.com/apps/rails-academy)

Once you see a successful message, you can continue to the next step.

### 2. Get into the lesson repository

First, let's make sure we are in the correct directory:

```bash
cd ~/lessons/ra-103
```

Next, we'll create a personal branch to work out of named after your Github username:

```bash
git checkout -b YOUR_GITHUB_USERNAME
```

A quick way to get your Github username is to run:

```bash
gh api user --jq '.login'
```

After that you should see a terminal like:

```bash
~/lessons/ra-103 [github_username]
$ _
```

### 3. Signup for DockerHub

#### Username

- Signup for a **free** account or login to [DockerHub](https://hub.docker.com/)
- Go to your Account Settings
- Copy your **username** from the top left next to your avatar or empty profile pic
- Open `~/config/deploy` in your editor and add the following

```yaml
# Name of the container image.
image: my-dockerhub-username/ra_103
```

And below also add your DockerHub username:

```yaml
# Credentials for your image host.
registry:
  # Specify the registry server, if you're not using Docker Hub
  # server: registry.digitalocean.com / ghcr.io / ...
  username: my-dockerhub-username
```

#### API Key

- Click on Personal Access Tokens
- Generate a new token with the following permissions (Read, Write Delete)
- Open `./.kamal/secrets` in your editor and add the following

```bash
KAMAL_REGISTRY_PASSWORD=your-personal-access-token
```

**Note::** This is not the most secure way to store your secrets, but it is the easiest for this lesson.

### 4. Configure Kamal to deploy your application

Now that you have your changes saved to git, you can deploy your application to a real server.

In `config/deploy.rb`.

Update the `server` line to be:

```yaml
servers:
  web:
    - your-github-username.rails.academy
```

Also change the `proxy` settings to:

```yaml
proxy:
  ssl: true
  host: your-github-username.rails.academy
```

And finally **uncomment** and set your user to your Github username:

```yaml
# Use a different ssh user than root
ssh:
  user: your-github-username
```

Finally run the following command to configure Kamal:

```bash
kamal config
```

If you see an error check `deploy.yml` for mistakes.

### 5. Generate a local rails master.key
    
```bash
EDITOR=nano rails credentials:edit
```

Save your changes by pressing `Ctrl + X` and then `Y` to confirm.

This will generate a private key in `config/master.key` required for rails to run.

### 6. Commit your changes to git

```bash
git add .
git commit -m "Added DockerHub and Kamal configuration"
```

### 7. :rocket: Deploy your application :rocket:

```bash
kamal deploy
```

If you don't see any errors you can now see your app running on the web.

`https://your-github-username.rails.academy`

:tada: You should see your application running. :tada:

### 8. Create a Pull Request

```bash
gh pr create
```

* Visit your PR on Github.

The automatic check will run if your code passes, you'll see:

:white_check_mark: All checks have passed

### :tada: You're Done! :tada:

#### Additional Resources

- :tv: [Kamal](https://kamal-deploy.org/)
- :tv: [Kamal 1.0](https://www.youtube.com/watch?v=yWSpjKErnco)
