# BrightHive DevOps Exercise - Logistics

## 1. Timeframe

If you are reading this document, then congratulations on making it to the technical portion of the interview! You'll be given  this assignment a few days ahead of your interview with the engineering team members. We want to be respectful of your time and fair to other candidates who may not have an extended amount of time to work on it. Please limit yourself to a maximum of **two hours**.

### 2. Acquire Exercise Code

You will need to clone the source code repository for the project that you will need to deploy for this assignment.

1. Create a Github account if you don't have one already. Please note that in the example below you will replace the username `user` with your own username.
2. Clone our repository to your local machine:

```bash
# Using SSH
$ git@github.com:gregmundy/trust-in-superheroes.git

# Using HTTPS
$ git clone https://github.com/gregmundy/trust-in-superheroes.git
```

### 3. Implement Solution

Implement your solution to the problem described [here](EXERCISE.md) using tools from the [technology stack](TECHNOLOGY.md).

### 4. Share Your Solution Via GitHub

Once you're done implementing your solution, you can place it in your own repository by adding it as a remote and pushing to it.

1. Create a new repository via the Github website. For discussion let's assume you named it `brighthive-solution`.
2. If possible, use a private repo. If you don't have private repos on Github, no problem, submit it as a public repository anyway. We just like to make sure that every candidate does their own work.
3. Add your repo as a remote and push. Note that if you use the HTTPS option (less preferred over SSH), you will need to provide your password on commit. Please remember to replace `user` with your Github username.

```bash
# Using SSH
$ git remote add myrepo git@github.com:user/brighthive-solution.git
$ git push myrepo master

# Using HTTPS
$ git remote add myrepo https://user@github.com/user/brighthive-solution.git
$ git push myrepo master
```

Give access to the following users: `gregmundy`, `tplagge`.

### 5. Contact Us

At least a day before your technical interview, email `greg@brighthive.io` the address of your repository.

### 6. Relax

The coding is done, the unit tests have been written, the product has been delivered. Now it's time to relax and get ready to meet with members of our engineering team.
