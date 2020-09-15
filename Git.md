
#### Manage commits in local repository until some work is finished

 1. Commit changes to local repository when your work is in progress.
 ```
 git commit -m "WIP"
 ```
 2. Keep on editing to the commit until your work is commited. (Ensure before each commit that project is in working state)
 ```
 git commit --amend --no-edit
 ```
 3. Commit to git when some work is finished
 ```
 git commit --amend -m "Implemented xyz"
 ```
#### Reset to a previous commit 

 ```
 git reset --hard
 ```
 or 
 ```
 git reset --hard HEAD
 ```
 
 
