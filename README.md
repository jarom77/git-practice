# Practice with git and GitHub

<img height="150" alt="git icon" src="https://github.com/user-attachments/assets/5df2e1d4-b754-450d-84f4-2d905f2401f6" />

This is a very simple repository for practicing with git and GitHub. git is a utility for *version control*. When a body of code is tracked with git, it is easy to see how the software has evolved over time, to roll back changes when needed, and to incorporate modifications by multiple collaborators. GitHub is a free online code hosting service that runs using git.

> ***Note***: There are many ways to use git. GitHub Desktop is one, and is used throughout this guide. VSCode also has an integrated git manager, which is very similar to GitHub Desktop. Git can also be used in the terminal - the commands are shown in a note like this in each section.

## Preparation

You should already have made an account on [GitHub](https://github.com/) and downloaded some form of git: [GitHub Desktop](https://desktop.github.com/), [Git Bash](https://gitforwindows.org/) (for Windows), [command-line git](https://git-scm.com/install), or [VSCode](https://code.visualstudio.com/download). 

## 1. Fork

<img height="150" alt="fork icon" src="https://github.com/user-attachments/assets/4df25223-68f0-4b6e-a82d-6362f1fc7df2" />

*Forking* refers to the act of creating your personal copy of an existing body of code. Typically you only do this for repositories that you don't have edit access to, such as this one. You can then modify your *fork* as you wish.

Go ahead and fork this repo, using the "Fork" button at in the top-right corner. 

Check out your fork! At the moment, it's just a copy of the [original repository](https://github.com/jarom77/git-practice) (which is a fork of another repo!). 

## 2. Clone

You now have a copy of this repository on GitHub. But how can you make changes? It's possible to manually edit files on GitHub, but this is not at all convenient. Instead, you should create a *local clone* of the repository. To do this, hit the big green button and choose Open in GitHub Desktop. Choose to create the repo in a location where you'll easily remember it. 

> Using the URL of the page, you can run `git clone <url>`, substituting the URL in.

## 3. Edit a File

In your local clone of the repository, open this file (`README.md`). At the top of the file, underneath the title, type 

```
I'm [your name] and I edited this file!
```

## 4. Add and Commit

Now go over to GitHub Desktop. Observe that the file `README.md` is now listed as changed. If there isn't already a blue checkmark beside the file, click the box to make one. 

> `git status` shows changes. `git add .` adds changes to all files in your repo. `git add <filename>` adds changes just for that file.

Then, add a *commit message* in the box below. The commit message should be a short description of what you achieved with your code modification. For example, a good commit message here might be "Add name to README.md." Once you've entered the commit message, click the big blue Commit button. 

> In command line, run `git commit -m "<message>"`

## 5. Branches

<img height="150" alt="image" src="https://github.com/user-attachments/assets/93626707-9d94-4e9f-8aee-123f91602ee6" />

Typically we don't commit directly to main as we just did. All work occurs on a branch that is specific to what you're currently working on. Let's make a new branch and do some development on it.

Run `git branch <branch_name>`, putting in an appropriate name for your branch. It's good practice to name your branch with your name and then a description of what you're working on, like `linus/tune-warp-drive`.

You can see that you have two branches now using `git branch`. However, you're still on "main". To switch to your branch, run `git checkout <branch_name>`.

Let's write some code! Make a new folder called `practice-folder` within the cloned repository. Then, create a Jupyter Notebook (or normal Python file) in this folder. Add the following code, obtaining a simple plot of a sine wave. 

```python
from matplotlib import pyplot as plt
import numpy as np

x = np.linspace(0, 2*np.pi, 1001)
y = np.sin(x)
f = plt.plot(x,y)
``` 

Make sure to save the resulting file. 

## 6. Add and Commit

Now, add (click the checkbox) beside your new notebook. Add an informative commit message, and commit the file. 

> You can add and commit as before, or you can do both in one command: `git commit -am "<message>"`. The -a means to add all files first.

## 7. Push

Great, we've made some local changes! Our primary remaining task is to *push* our code back to GitHub. This will allow us to share our code with others.

To push your code, just click the black "Push" button at the top right of GitHub Desktop. Before you click, you can notice that the button indicates the number of commits that you have made since your last push. After you click the button, you will have no more commits to push.

> `git push` pushes the current branch, `git push --all` pushes all branch changes. The first time you push a new branch, you will need to run `git push --set-upstream origin <branch_name>` so git knows to create the branch on Github.
>
> Using the command line requires you to authenticate when interacting with the remote (github.com), as you do that during setup in Github Desktop. Just type in your username and password.

## 8. GitHub Pull Requests

<img height="150" alt="image" src="https://github.com/user-attachments/assets/dbbe7787-c63b-4dfa-9b4e-f155439cceaf" />

Now go to the URL of your fork on GitHub and inspect the new `README.md` file. You'll notice that your new folder isn't there! Click on the dropdown near the top and select your branch. Now your folder is there! You can also take a look at the Jupyter Notebook you created. Note a nifty feature: by default, GitHub renders the Jupyter Notebook, so that you can see the plot you created. Your code is also shown in an attractive and readable format.

How can you get the changes to `README.md` and your Python on the same branch though? We need to perform a *merge* using a *pull request*. Click on "Pull Requests" in the top bar, and click the green button "New Pull Request". If a "base repository" is listed, change it to your own fork (the one with your username). We're merging the changes *from* the branch on the right *to* the branch on the left, following the arrow. So "main" should be on the left and your new branch on the right. Add a title for the changes, and list any pertinent information in the description, such as which files were changed, what was changed, and why. It's also helpful to include what kind of testing you did to ensure your code works. Create the pull request.

Pull requests can be reviewed by other team members and they can leave comments. Once everyone is satisfied that these changes aren't going to break anything, you can finish the merge. Now all your changes are together on "main".

## 9. Pull

What if there's a change made on GitHub that's not present in your local repository? This is a common situation when collaborating. Your partner made some cool improvement to the code that you would like to access. To do this, you need to *pull*. 

Let's incorporate the merge we just did into our local repository. In GitHub Desktop, the button that used to say "Push" should now say either "Fetch" or "Pull" with an indicator of how many commits there are to be pulled. If it says "Fetch," you should click it once and wait for it to say "Pull." Once it says "Pull," click it again and wait a few moments for the pull to complete.

> Make sure you're on the right branch, and then run `git pull` to get the changes on that branch. In this case, you need to be on "main". You can also run `git pull --all` to get changes for all branches.

Finally, check that your new folder is in your repo again. Your merge online is now reflected in your own files - "main" has all the changes.

<details>
<summary><h2>Further Reading</h2></summary>

An important principle of version control is that you **never** duplicate files. Rather than having `first_draft.ipynb`, `final_version.ipynb`, `final_version_REAL.ipynb`, you should instead commit your code at each stage (or even more frequently). You'll always be able to go back and find the earlier versions in the commit history.

Another topic that you might find useful to explore on your own is the `.gitignore` file. This file specifies files which should be *excluded* from tracking by git. This is handy if there are certain "junk" files that you would prefer not to see in GitHub. 

Finally, if you're using the command line, you can do some reading on how to set up SSH keys so you don't need to type in your username and password each time.

## Discard and Revert

One huge advantage of working with a version control system like git is that you can easily undo mistakes by going back to the last "good" version of your project. There are multiple ways of doing this. We'll focus on two. 

### If You Haven't Committed Yet: Discard

So, you were making a small tweak to your file and accidentally broke the amazing function that you were working on. It happens! If you catch this before you commit your changes, then fixing it is easy -- all you need to do is *discard* your changes. 

In that Jupyter notebook you created in Step 5, delete the line `import numpy as np`. Now your notebook won't correctly generate the plot (after resetting the kernel). Whoops! Pretend that you didn't notice, and save the notebook. 

Over in GitHub Desktop, notice that there is a change recorded to that file. Right-click on the change and choose "Discard Changes." Check your notebook again. You should observe that the line `import numpy as np` is back where it belongs. Great!

### If You Committed Your Mistake: Revert

Sometimes, we don't catch a mistake until after we've already committed it. If we're unlucky, we may even have created other commits since our mistake. In these cases, the first step is to identify on which commit the error was introduced. This requires careful debugging and attention to detail. One approach is to *go back* to a previous commit on which you know your code was working, and then step through the changes you made. To do this, we use the *revert* command. 

Go back to your Jupyter Notebook, and delete `import numpy as np` again. This time, commit the change, with commit message "remove numpy import." Oops! Now our committed code is broken. 

To *revert* the commit, navigate over to the History tab of GitHub Desktop. Right-click the commit with the message "remove numpy import," and choose "Revert Changes in Commit." This will have the effect of creating a *new* commit that undoes the changes in your erroneous commit. This will work even if you've made other commits since the bad one; only the changes from the bad commit will be reverted. 

***Note***: GitHub Desktop doesn't gave an option corresponding to `git reset`, but if you are comfortable in the terminal and familiar with this command, you can also use `git reset` to accomplish a similar task, albeit with different consequences for your commit history.
</details>
