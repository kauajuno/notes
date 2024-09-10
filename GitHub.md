GitHub is a website that provides web hosting for git repositories, being the most used choice for this purpose. Putting that in simple terms, it is a website to which people can upload their git repositories.

# Uploading your first git repo to GitHub

In order to upload a repository to GitHub, first you need to create and login to a GitHub account. After that, hit the plus button and then **new repository**. For this first time, create it with all the default settings on initialization.

After creating your GitHub repository, you need to upload one of your local git repositories to it, an action called **push** in the git context. In order to do that, first you need to configure the local repository to tell it where you're going to **push** your commits.

This is done through the commands:

```
git remote add origin [https-link-provided-by-github]
```

Then you can start pushing your content to that repo:

```
git push -u origin main
```

Summarizing everything: just follow the instructions provided by GitHub and you'll be good.

>[!info] What's all these letters?

