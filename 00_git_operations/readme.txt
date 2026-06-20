Git Workflow: Cloning, Editing, and Merging Branches
This guide outlines the step‑by‑step process for cloning a repository, making changes, and merging a feature branch into the main branch.

1. Clone the remote repository
>> git clone <repository-url>

2. Navigate into the repository folder
>> cd <repository-name>
 
3. Create a new branch
Use a clear naming convention such as dev/branch_name:
>> git checkout -b <new-branch-name>

4. Check the current status
>> git status
Unstaged files and folders appear in red.

5. Stage all changes
>> git add .

6. Verify staging
>> git status
Staged files and folders appear in green.

7. Commit the changes
>> git commit -m "Describe the changes made" 

8. Push the new branch to the remote
>> git push -u origin <new-branch-name>

9. Switch to the main branch
>> git checkout main 

10. Update the local main branch
>> git pull origin main

11. Merge the feature branch into main
>> git merge <feature-branch-name>
