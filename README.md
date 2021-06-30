# Handling a Git Merge Conflict

In this exercise, you and a partner will make different changes to the same MarkDown document. This will generate a Merge Conflict, which you must then resolve.

## Instructions

### Working as an owner
1. Choose a partner
2. Give your partner a link to this GitHub repository
3. Clone your repository to your development machine. (Choose carefully which folder you use to hold your local repository.)
4. You will be the owner of your own repository.
5. Imagine that you have spoken with the client, and that you are acting with autority.
6. Checkout the `dev` branch
7. Hide the bug by removing the style from the span, so that it no longer appears red.
8. Make some changes to your local repository. For example:
   * Choose a different banner image
   * Change the header
   * Change the list from a bulleted list to a numbered list
   * Add a paragraph of text
9. Use `git add .` to add your changes to git's staging area
10. Use `git commit` to commit your changes
11. In the commit message:
   * Create a short descriptive title
   * Provide details of all the changes that you have made
12. Checkout the `main` branch.
13. Merge the changes from the `dev` branch

### Working as a team member
1. Fork the repository for which your partners sent you a link
2. Clone your fork to your development machine. **Choose carefully which folder you use to hold your local repository. Do NOT put it inside the same folder as the repository for which you are the owner.**
3. Create a new `upstream` remote for your repository using the Code link from the URL your partner sent you.
4. Imagine that you have spoken with the dev team, and that you have to make an important bug fix, and also make some minor changes.
5. Create a new branch with a name that describes the feature that you are planning to work on.
6. As above, make some changes to your local fork. For example:
   * Fix the bug
   * Choose a different banner image
   * Change the header
   * Change the list from a bulleted list to a numbered list
   * Add a paragraph of text
7. Use `git add .` to add your changes to git's staging area
8. Use `git commit` to commit your changes
9. In the commit message:
   * Create a short descriptive title
   * Provide details of all the changes that you have made
10. Push your changes to your fork:
   `git push origin <name-of-your-feature-branch>`
11. Go to your GitHub fork and create a Pull Request for your changes.

### Working as the owner
When you receive notification of the PR created by your team member:
1. Visit your (authoritative) repository on GitHub
2. Click on the Pull Request tab
3. **Do not automatically merge the PR**. Instead, click on the link and copy the lines of code that allow you to pull the proposed changes to your development machine.
4. Make sure that the pull is based on the `dev` branch
5. Make sure that you are working in the branch created by your team member
6. Work through the Merge Conflict procedure. Remember: you are the owner. You have responsibility to the client. Choose which incoming changes to keep and which to reject.
7. When you are satisfied, commit the changes. You will see an automatically generated message. Why is it red? Why should you not use this?
8. In the commit message:
   * Create a short descriptive title
   * Provide details of all the changes that you have made
9.  Hold a meeting with your team member, to reach consensus on what should be merged to the `dev` branch.
10. Checkout the `dev` branch
11. Merge the changes from the feature branch. You will need to provide a commit message.
12. Push the updated `dev` branch to your GitHub repository
13. Ask your team member to pull the changes from the `dev` branch.


### Working as team member
When you receive notification from the owner that the `dev` branch has been updated:
1. Checkout the dev
2. Run `git pull upstream dev`
3. Check that everything looks the way you expected after your discussions with the owner. If not, start the cycle again.


### Working as the owner
When you receive notification from your team member that the `dev` branch is now operational:
1. Checkout the `main` branch
2. Merge the changes from the `dev` branch. You will need to provide a commit message.
3.  Push the updated `main` branch to your GitHub repository
4.  Tell your team member that the changes have gone live.
