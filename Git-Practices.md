
# Git Practices

## Assignment 1: Branch Operations

### Create Branch

**1. How do you create a new branch in GitLab using the web interface?**

- Step 1: Click on “New Project” to create a new project.  
- Step 2: Click on the “+” icon, then under “This repository”, click on “New branch” to create a new branch.  
- Step 3: Enter a branch name and select the source branch (typically main or master).  
- Step 4: Click “Create branch”.

**2. What steps do you follow to create a Merge Request (MR) in GitLab via the GUI?**

- Step 1: Go to your GitLab project and click on “Merge Requests” in the left menu.  
- Step 2: Click on “New merge request”.  
- Step 3: Select the source branch (the one you want to merge) and the target branch (usually main).  
- Step 4: Click “Compare branches and continue”.  
- Step 5: Fill in the title, description, and optionally assign reviewers or labels.  
- Step 6: Click “Create merge request”.

**3. How can you squash commits in a Merge Request before merging in GitLab?**

- Step 1: Open the Merge Request.  
- Step 2: Scroll down to the merge section.  
- Step 3: Check the box labelled “Squash commits when merge request is accepted.”  
- Step 4: Click “Merge” when ready.

**4. What is the process to revert a commit using the GitLab web interface?**

- Step 1: Go to your GitLab project and click on “Branches” from the “Code” dropdown in the left menu.  
- Step 2: Find the commit you want to revert.  
- Step 3: Click “Options” in the top right and select “Revert.”  
- Step 4: GitLab will prompt you to create a new merge request for the revert — confirm the options and proceed.  
- Step 5: Fill in the title, description, and optionally assign reviewers or labels.  
- Step 6: Click “Create merge request.”

**5. How do you delete a merged branch in GitLab using the GUI?**

- Step 1: Go to your GitLab project and click on “Merge Requests” from the “Code” dropdown in the left menu.  
- Step 2: Select the branch you want to delete.  
- Step 3: If it has already been merged, click “Delete branch” from the three dots on the right side.  
- Step 4: A confirmation message will appear, click “Yes, delete branch.”

...

## Assignment 4: Advanced Git Concepts

### Git Hooks

**1. Write a pre-commit hook that checks for code style violations before allowing a commit.**

*(Implementation not provided in source document)*

### Git Bisect

**1. Simulate a bug in your project history.**  
**2. Use `git bisect` to find the commit where the bug was introduced.**
