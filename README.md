## Rails Academy: Lesson 102 - Hello World Deployed

At the end of this lesson you with have a created your first rails project deployed to a real server.

This will create a **free server** that you can use for the other lessons or your own projects.

### Topics

- Rails New
- Rails Controllers
- Rails Views
- DockerHub
- Kamal

### Prerequisites

[Lesson 101](https://github.com/justintanner/ra-101)

### 1. Install the Rails Academy GitHub app

**If you haven't already [added your ssh keys](https://github.com/justintanner/ra-101?tab=readme-ov-file#2-generate-a-local-ssh-key) from the previous lesson, please do so now.**

- Login to your [GitHub account](https://github.com)
- Install the [Rails Academy GitHub App](https://github.com/apps/rails-academy)

While your server is starting up, lets get to hello world locally.

### 2. Get into the lesson repository

First, let's make sure we are in the correct directory:

```bash
cd ~/ralessons/ra-102
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
~/ralessons/ra-102 [github_username]
$ _
```

### 2. Create a new rails project

Still in the `ra-102` directory, run the following command to create a new Rails project:

```bash
rails new . --skip-git
```

This will create a new Rails project in the current directory, skipping git because the lesson already has a git repository.

Now lets our ruby gems by running:

```bash
bundle install
```

### 3. Launch a local server

```bash
rails server
```

Visit [http://localhost:3000](http://localhost:3000) in your browser to see your new app running with the default Rails welcome page.

### 4. Save your changes to git

```bash
git add .
git commit -m "Installed Rails"
```

### 5. Create a home controller

```bash
rails generate controller home index
```
This will create a new controller called `home` with an action called `index`.

### 6. Update the routes

Open the `config/routes.rb` file and add the following line
    
```ruby
root 'home#index'
```

This will set the `home#index` action as the root of the application.

### 7. Update the view

Open the `app/views/home/index.html.erb` file and add the following line:

```html
<h1>Hello World</h1>
```

### 6. Double check your work

Start the local server by running:

```bash
rails server
```

If you see "Hello World" on [http://localhost:3000](http://localhost:3000) it's working.

### 7. Save your changes to git

```bash
git add .
git commit -m "Added home controller"
```

### 8. Signup for DockerHub and get your API KEY

- Signup for a **free** account or login to [DockerHub](https://hub.docker.com/)
- Go to your Account Settings
- Click on Personal Access Tokens
- Generate a new token with the following permissions (Read, Write Delete)
- Open `./.kamal/secrets` in your editor and add the following

```bash
KAMAL_REGISTRY_PASSWORD="yourkeygoeshere"
```
.. more comming

### 9. Configure Kamal to deploy your application

Now that you have your changes saved to git, you can deploy your application to a real server.

Open the file `config/deploy.rb`.

Update the `server` line to be:

...

### 9. Deploy your application

```bash
kamal deploy
```

Now open your browser and visit your sandbox URL such as `https://github-username.rails.academy`.


### 10. Create a Pull Request

```bash
gh pr create
```

* Visit your PR on Github.

The automatic check will run if your code passes, you'll see:

:white_check_mark: All checks have passed

### :tada: You're Done! :tada:

#### Additional Resources

- :tv: [Ruby on Rails](https://rubyonrails.org/)
- :tv: [Kamal](https://kamal-deploy.org/)
- :tv: [Kamal 1.0](https://www.youtube.com/watch?v=yWSpjKErnco)


