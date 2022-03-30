# Handling a Git Merge Conflict

In this exercise, you and a partner will make different changes to the same MarkDown document. This will generate a Merge Conflict, which you must then resolve.

### Please be sure to read [the context of this exercise](./Context.md) before you continue. 

---
## Your Mission, if You Decide to Accept It...

This exercise will walk you through all the steps described above, and will deliberately create a merge conflict, that you must resolve.

This way, you will get experience in:

* The regular workflow of a project managed with GitHub
* Dealing with an unexpected issue calmly and professionally.

---
## Instructions

The exercise is in four parts, and there are two roles: owner and team member. You can work through the exercise twice: the first time, one of you will be the owner, the other will be the team member. The second time, you can switch roles.

You can take it in turns to share your screen with your partner, as you work on your specific part.

### Part 1: Working as an owner, making changes to `dev`

1. _You are be the owner of this GitHub repository. You will be the only person with admin rights to it. Only you can `push` to this repository._
2. Clone this repository to your development computer. (Choose carefully which folder you use to hold your local repository.)
3. `cd` into your cloned repository
4. Open the repository folder in VS Code
   ```bash
   code -r .
   ```
   Or in plain English: "VS `code`, `-r`euse this window to open `.` (= this folder)"
5. Open a Terminal pane (`Ctrl-` `)
6. For technical reasons, the repository currently contains only a `main` branch. Start by creating a `dev` branch from the `main` branch:
   ```bash
   git checkout -b dev
   ```
   The `dev` branch should now be identical to the `main` branch.
7. Push the `dev` branch to your (owner's) GitHub repository:
   ```bash
   git push origin dev
   ```
8. Choose a partner
9.  Give your partner a link to this GitHub repository. Copy the link from your browser's address bar. Your partner can now start to follow the **Working as a team member** steps below.

Imagine that you have spoken with the client, and that you are acting with authority. You are now going to create a new branch, make some changes, and test them locally.

10. Create a new branch called `client-requested-changes`
   ```
   git checkout -b client-requested-changes
   ```
11. Open the `sourceOfConflict.md` file. Notice that it contains a "bug" which will appear in red if you preview the MarkDown text.
12. Provide a _cosmetic_ fix for the "bug" by removing the style from the span, so that it no longer appears red. But the bug is still there. It's just hidden. So don't change the text. It should look like this:
   ```html
   <p>There is a bug in this file.<p>
   ```
13. Make some other changes as you like. For example:
   * Choose a different banner image
   * Change the header
   * (Leave the list as it is)
   * Add a paragraph of text
14. Run `git status` to see which files have changed
15. Run `git diff` to see which files have been edited
16. Use `git add .` to add your changes to git's staging area
17. Use `git commit` to commit your changes (but read [this](https://github.com/DCIForks/E07/wiki/Good-git-commit-messages:-using-VS-Code-as-your-git-editor) first).
18. When writing the commit message:
   * Refer to the output of the `git status` and `git diff`
   * Create a short descriptive title
   * Provide details of all the changes that you have made as bullet points
   * Remember that you know the context of what you are writing, but other readers (including yourself in 3 weeks' time) will not know the context. So make your notes clear and detailed.
   
   For example, your commit message might look like this:
   ```markdown
   Apply client-requested changes

   * Alter banner image
   * Use text given by client for the header
   * Add paragraph provided by client
   ```
19. Run `git log` to check that your commit was correctly applied, and that your commit message is clear.
20. *Only if necessary* you can run `git commit -amend` to correct any mistakes in your commit message.

You should now have:
* The original `sourceOfConflict.md` file in `main`
* The original `sourceOfConflict.md` file in `dev`
* Your updated `sourceOfConflict.md` file in the new `client-requested-changes` branch.

Your work as owner is done, for now.
    
---
### Part 2: Working as a team member, making changes in a `bug-fix` branch
1. Visit the link to your partner's repository which they sent you in step 9 above.
2. Near the top left of the repository's main page, you should see a button named Fork. Click on this to create a fork of your partner's repository.
3. If given a choice of accounts to which to fork the repository, choose your own personal account.
   
   If your partner's repository is found at a URL like...  
   [https://github.com/DCI_group/Merge-Conflict-owner]()  
   ... then your fork should be created at a URL like:
   [https://github.com/your_name/Merge-Conflict-owner]()  


A _fork_ is like a _clone_, but not exactly. Like a clone, it is an identical copy of the original repository. However, a fork will live on GitHub, while a clone lives on your local development computer.

You will have __read-write access_ to your fork, but only _read access_ to your partner's (owner's) repository. This means that you cannot push any changes to the owner's repository. You need to fork it, so that you have your own copy of the repository, so that you can push your work to GitHub. As you will see, GitHub will then suggest that you create a _pull request_ for your partner to review.

4. Clone your fork to your development computer.

   **Choose carefully which folder you use to hold your local repository. In particular, do NOT put it inside the same folder as the repository for which you are the owner.**
5. Use `git remote -v` to check what remote Git repositories your local repository is connected to. (The `-v` means "verbose", which makes Git show the path as well as the name of the remote.) You should see something like:
   > ``` bash
   > origin    git@github.com:your_name/Merge-Conflict-owner.git (fetch)
   > origin    git@github.com:your_name/Merge-Conflict-owner.git (push)
    
   In other words, you should have a remote called `origin` which points to your GitHub fork on your personal GitHub account from which you cloned this local repository.

You now need to tell Git where the owner's original "source of truth" repository is. By convention, the name for a Git remote that _you_ own is `origin`. By convention, the name for the "source of truth" repository is `upstream`.

6. In your browser, visit the link that your partner sent you earlier (the page from which you forked your GitHub repository).
7. Click on the green Code button and copy the path that _would_ allow you to clone the repository (but don't clone it).
8. In the Terminal window for your local clone, run the following command:
   ```bash
   git remote add upstream <clone-link-that-you-just-copied>
   ```
   **Note that you should replace `<clone-link-that-you-just-copied>` with the actual link that you just copied, so your command might look like this:
   ```bash
   git remote add upstream git@github.com:DCI_group/Merge-Conflict-owner.git
   ```
9. Run `git remote -v` again. You should now see something like: 
    
   > ``` bash
   > origin    git@github.com:your_name/Merge-Conflict-owner.git (fetch)
   > origin    git@github.com:your_name/Merge-Conflict-owner.git (push)
   > upstream      git@github.com:DCI_group/Merge-Conflict-owner.git (fetch)
   > upstream      git@github.com:DCI_group/Merge-Conflict-owner.git (push)


Imagine that you have spoken with the dev team, and that you have to make an important bug fix, and also make some minor changes. To do this, you are going to create a new branch based on the `dev` branch, and make your changes in that.

10. Check what branches you have locally. Run `git branch -v`. (The `-v` means `v`erbose, so Git will print out both the id and the title of the latest commit message for each branch.)
11. You are likely to see only a `main` branch. It might look something like this:
    ```bash
    * main cdd7c29 Initial commit
    ```
12. To see all the branches that are available on your remote GitHub fork, run `git remote -r` (where `-r` means `r`emote). You should see something like this:
    ```bash
    origin/HEAD -> origin/main
    origin/dev
    origin/main
    ```
    Note that the `dev` branch was not visible when you ran `git remote -v`, because you had not yet checked it out locally.
13. Create a new branch with a name that describes the feature that you are planning to work on. You can give this branch any name you like but make sure that it is descriptive of the changes that you plan to make. I'll call it `bug-fix`. Base this on the current `dev` branch:

   `git checkout -b bug-fix dev`

__This command says: "`git`, please `checkout` a new `-b`ranch called `bug-fix` and copy the current contents of the `dev` branch into it, as the starting point"._

6. As the owner did above, make some changes to your local fork. You want to ensure that you generate a merge conflict later, so make sure that your changes are different. For example:
   * To "fix" the bug, remove the style, edit the text to...
     ```
     <p>There is no bug in this file</p>
     ```
   * Leave the banner image as it is
   * Change the header
   * Change the list to a numbered list
7.  Run `git status` to see which files have changed
8.  Run `git diff` to see which files have been edited
9.  Use `git add .` to add your changes to git's staging area
10. Use `git commit` to commit your changes (but read [this](https://github.com/DCIForks/E07/wiki/Good-git-commit-messages:-using-VS-Code-as-your-git-editor) first).
11. When writing the commit message:
   * Refer to the output of the `git status` and `git diff`
   * Create a short descriptive title
   * Provide details of all the changes that you have made as bullet points
   * Remember that you know the context of what you are writing, but other readers (including yourself in 3 weeks' time) will not know the context. So make your notes clear and detailed.
   
     For example, your commit message might look like this:
     ```markdown
     Fix bug, header and list type
  
     * Alter header as agreed with dev team
     * Change bullet list to number list
     * Fix bug
     ```

---
> This is currently the state of the project:
> * There are four repositories:
>   1. The owner's local repository on their development computer
>   2. The owner's authoritative repository on GitHub (`upstream`)
>   3. Your fork of the authoritative repository  on GitHub (`origin`)
>   4. Your local clone of the forked repository
>
> * The two repositories on GitHub (2, 3) share identical content
> * The owner's local repository (1) contains changes to the `client-requested-changes` branch
> * The owner's local repository (1) and your local repository (4) both contain both `main` and `dev` branches which are identical to the GitHub repositories' (2, 3)
> * Your local repository contains a new `bug-fix` branch.
> * Your `bug-fix` branch and the owner's `client-requested-changes` are different.
>
> The following steps will allow your `bug-fix` branch to travel first to your GitHub fork (3), then to the owner's GitHub repository (2), so that the owner can pull your changes to the repository on their development computer to test and review it.

---
1.  Push your changes to your fork:
   `git push origin bug-fix`
14. Go to your GitHub fork in your browser and click on the green Compare & Pull Request button that should have appeared.
15. If you don't see this button:
    * Refresh the page
    * Ensure that the Pull Requests tab is active
    * Ensure that the `bug-fix` branch is selected.
16. Check that the automatically created message is meaningful, and if not, edit it. Add a personal note, if you want.
17. Click on the green Create Pull Request button.
18. GitHub will probably now take you to the page for the owner's repository.

> In a real project, you might in fact make a number of commits and push them all to your local fork before you make the Pull Request. This is why GitHub does not generate the Pull Request automatically, but waits until you are ready.

---
### Part 3: Working as the owner: reviewing the pull request
Owner, when you receive notification of the PR created by your team member:
1. Visit your repository on GitHub
2. Click on the Pull Request tab
3. If there is a Feedback PR, you can ignore it: this would have been generated automatically by GitHub Classrooms, so that your mentors can provide you feedback on your work.
4. Click on the most recent pull request. Its name could be either the title that your team member used for the most recent commit message (e.g. "Fix bug, header and list type"), or a prettified version of the branch name (e.g. "Bug Fix").

![Pull Request page](screenshots/pullrequest.png)

> GitHub helpfully provides a big green Merge Pull Request button but **do NOT click on this**. This button allows you to merge the pull request directly in GitHub, but it does not give you the chance to test that everything is working correctly with the changes that you made locally earlier.
> The big green button is only useful for treating very minor changes that you can safely make directly to the `main` branch without any testing. Indeed, it would be probably be disabled for any changes that resulted in a conflict.
>
> Instead, click on the link to view `command line instructions` and review the lines of code for Step 1. These are designed to allow you to pull the proposed changes to your development computer, but they are not exactly what you need, so you will need to edit them.
> ![Command Line Instructions](screenshots/cli.png)
> The automatically generated code creates a new branch based on `main`, but you want to check that everything is compatible with your custom `client-requested-changes` branch.

1. Copy the first line of code for Step 1 **without the final `main` branch name** and paste it into the Terminal in VS Code. Press Enter to execute this command. It might look something like this:

   ```bash
   git checkout -b partner-bug-fix
   ```
   
   **Note**: This command will copy the current state of your `client-requested-changes` into a new branch. If the command fails, run `git status`, to check that you haven't made any changes since the last commit, and if you have, run `git add . && git commit` and write a meaningful commit message before you try executing the line of code that you just pasted again.

   **Note**: *Only if you **do*** include the `main` branch name by mistake, your new branch will be a copy of the unchanged `main` branch, with none of your changes. To fix this run:
   ```
   git merge client-requested-changes
   ```
2. Go back into your browser and copy the second line of code from Step 1 and paste it into the Terminal pane, then press Enter. This will pull the changes from your team member's feature branch.
   
   **Note**: `pull` is actually a shortcut for two Git commands: `fetch` followed by `merge`. The `fetch` command will get the data from your partner's feature branch on their GitHub fork repository; the `merge` command will do its best to apply all your partner's changes to your current branch.

## Merge Conflict!

As planned, this implicit `merge` command will fail. It fails because both you and your partner have made changes to the same lines of the same file.

> In a real project, all the team members will do their best to work on separate files, so merge conflicts should only occur in exceptional circumstances. But you are just about to learn how to handle such exceptional circumstances, so that everything will go smoothly even when the unexpected happens.

![Merge Conflict](screenshots/conflict.png)

1. In the VS Code editor, you should now see both your version and your collaborator's version, against a coloured background.
2. Just above the coloured zones, you will see a number links: [Accept current changes]() | [Accept incoming changes](), and so on. Click on one of these to see what happens. Press Ctrl-Z to undo your action and restore the Merge Conflict display.
3. Hold a meeting with your team member, to reach consensus on how to resolve this conflict.
4. Remember: you are the owner of this project. You have responsibility to the client. Your decision is final. You will need to:
   * Choose which incoming changes you want to accept
   * Choose which current changes you want to keep
   * Ensure that the three lines...
     ```
     <<<<<<< HEAD (Current Change)

     =======

     >>>>>>> longIdStringMadeOfRandomLettersAndNumbers (Incoming Change)
     ```
     ... are deleted.
5. When you are satisfied, commit your changes. You will see an automatically generated message.
   > Question: Why is it red? Why should you not use this exactly as it stands?  
   >  
   > Answer: In a commit message, you should:
   > * Create a short descriptive title  
   > * Provide details of all the changes that you have made  
   > If the first line (the short descriptive title) is more than 50 characters long, VS Code will helpfully display it in red, to warn you that it is too long. (You _can_ ignore this warning if you want.)
   
---
The custom branch that you have just created (`partner-bug-fix`) now holds the most up-to-date version of your project. Now you need to share this with all your team members, so that they can synchronize their work with yours.

1.  Checkout the `dev` branch
2.  Merge the changes from the custom branch you were just working on. Your Git command might look something like this:
    ```bash
    git merge --no-ff partner-bug-fix
    ```
    * `--no-ff` means `no f`ast `f`orward. This tells Git to work safely and to show errors if there is any difficulty with the merge.
3.  Push the updated `dev` branch to your GitHub repository
    `git push origin dev`
4.  Ask your team member to pull the changes from the `dev` branch.

---
### Part 4: Working as team member, updating your repositories
When you receive notification from the owner that the `dev` branch has been updated:
1. Checkout the `dev` branch
2. Run `git pull upstream dev`
3. Check that everything looks the way you expected after your discussions with the owner. If not, go through this cycle again.
4. Finally, push the updated version of your `dev` branch to your GitHub repository.

> Now, all 4 repositories should be in the same state. In all the repositories...
> 
>   1. The owner's local repository on their development computer should have the original `main` branch still unchanged
>   2. The owner's authoritative repository on GitHub (`upstream`)
>   3. Your fork on GitHub of the authoritative repository (`origin`)
>   4. Your local clone of the forked repository
> 
> ... the `main` branch will be unchanged, and the `dev` branch will have been updated.

The only differences will be that the owner's local repository will have two custom branches...
* `client-requested-changes`
* `partner-bug-fix` 
... and the team member's local repository and GitHub fork will have one custom branch:
* `bug-fix`

If all is well, these branches will have outlived their usefulness and you can now delete them:

5. If you are the owner, you can run:
   ```bash
   git branch -D client-requested-changes partner-bug-fix
   ```
6. If you are the team member, you can run:
   ```bash
   git branch -D bug-fix
   git push origin --delete bug-fix
   ```
   * The `-D` directive says "delete this branch even if it is unmerged". The second command deletes the `bug-fix` branch on the remote `origin` repository on GitHub.

You are now ready to start a new cycle of development. This would start with checking out a new branch with a different custom name, describing the next feature you want to work on.

## A New Release

When everyone on the team is satisfied that the `dev` branch is ready to be released to end-users, the owner can run `git checkout main && git merge dev && git push origin main` on their local computer. This will update `main` locally and push it to the "source of truth" GitHub repository.

Now all the other team members can run `git checkout main && git pull upstream main && git push origin main && git checkout dev && git merge main`. This will...

* Pull the latest version of `main` to their local computers
* Synchronize `main` on their remote GitHub forks
* Make `dev` locally identical to the current `main`

... ready to begin work on the next version.


