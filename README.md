# Stateless repos? 🤷
Stateless? Yes. Stateless. Those who know me––and know me well––know that I'm (too) opinionated! And more so opinionated about software, because software is a new, super powerful expression that we can all share, but is tormenting when it does too little or too much.

One such expression of software 'doing too much' is how GitHub thinks about repos. To me, a repo is a one-stop shop to browser source code and decide whether or not to experiment with some piece of software. This is all good and fair, but what drives me mad is commits. Commits man, I don't need 'em!

Commits? Yes––when I'm perusing a repo, all I care about is the current state of the project; (most times) I don't care about who contributed, for what reason, or when; e.g. I don't care about the commit messages. Call me sadistic, but all I want is the project in its current state. In other words, the 'stateless' repo.

Of course, **this is just a personal preference**. This might not be desirable for a lot (if not most) people. Software versioning is fundamental, but to me––as an end-user and prospective consumer––it's junk, and makes me feel all the more uncomfortable to use it. Too much information can be a bad thing, too.

So all that being said, I do believe that versioning matters and has a place in all this, just not on the front page. So now that this rant is coming to a close, let me share some techniques I learned and used to author what I'm calling stateless GitHub repos, and share one other weird trick for serving repos!

# Here's how 💡
Once a GitHub repo is initialized with an initial commit (doesn't matter––it'll be deleted), we can continue to use Git to cover our tracks and hide ~dead bodies~ commits from prospective users. As a precaution, please first test this on a new repo to understand how it works. OK, so here's how:

```
git checkout --orphan latest_branch       &&
git add -A                                &&
git commit -a --allow-empty-message -m '' &&
git branch -D master                      &&
git branch -m master                      &&
git push -f origin master
```

Don't expect me to now explain this code because, to be honest, I have no idea how it works. 🙈 But I know that it works! And that fact that it works means that it's repeatable. So once this command is run, the current state is kept and previous commits are deleted. And (of course) this can be repeated for each (new) state.

You can learn more about this technique here: https://stackoverflow.com/a/26000395.

# One other weird trick... 🙊
There's one other (weird) trick I just learned that, when coupled with stateless repos, maximizes GitHubs usefulness for me. That is, accessing a repo as a webpage. For frontend developers, **all we want is to build and ship websites to some public-facing URL for testing and sharing**.

[GitHub Pages](https://pages.github.com) attempted to solve this dilemma, but is limited to one(!) repo per user. What comes in ones?? Nature doesn't even come in ones!! ~One is a prime number~ and just doesn't cut it. We author dozens of websites––not one––and so we need a better solution.

First, I tried [Scrimba](https://scrimba.com), but that doesn't work the weird DOM-injection techniques I just came up with. I tried [CodePen Projects](https://blog.codepen.io/2017/03/20/codepen-projects-is-here), but that is limited to frontend files (e.g. not Go files––hacking this doesn't work, I tried) and is also limited to one per user. What is it with this number?? And then I had an idea; [RawGit](https://rawgit.com).

RawGit is interesting, because with it, we can transform repos into websites. All we need to do is circumvent the headers GitHub returns on request. This is the difference between viewing a file as source code and viewing as a website. Wait. ... You're telling me all this was possible **the whole time** were it not that GitHub flubbed some headers?? Yes!

You can learn more about this technique here: https://stackoverflow.com/a/6218255