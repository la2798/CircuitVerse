## Contribution Guildlines
## Steps to make your first pull request
- Fork the project

![alt test](https://help.github.com/assets/images/help/repository/fork_button.jpg)

- Clone your local project

![alt test](https://help.github.com/assets/images/help/repository/https-url-clone.png)

Open gitbash and type the following
```
$ git clone https://github.com/CircuitVerse/CircuitVerse.git
```
- Navigate into your new cloned repository
```
cd CircuitVerse
```
- To see that your local copy has a reference to your forked remote repository in github, run the following command
```
$ git remote -v
```
You should see the following output:
```
origin https://github.com/your_username/CircuitVerse.git (fetch)
origin https://github.com/your_username/CircuitVerse.git (push)
```
Now add a reference to the original CircuitVerse repository
```
$ git remote add upstream https://github/CircuitVerse/CircuitVerse.git
```
See the changes using
```
$ git remote -v
```
```
origin https://github.com/your_username/CircuitVerse.git (fetch)
origin https://github.com/your_username/CircuitVerse.git (push)
upstream https://github.com/CircuitVerse/CircuitVerse.git (fetch)
upstream https://github.com/CircuitVerse/CircuitVerse.git (push)
```
- Sync it
In a regular interval and **before making any changes**, run the following commands **carefully** to update your local repository
```
# to fetch all remote repositories and delete any deleted remote branches
$ git fetch --all --prune

# switch to master branch
$ git checkout master

# Reset local master branch to match upstream repository master branch
$ git reset --hard upstream/master

# Push the changes to your forked repo
$ git push origin master
```
- Create a new Branch
After completing the above steps, you are good to start contributing to our Issues. Please create a ```seperate branch``` and **keep your master branch clean**
```
# To create a new branch and switch to it
$ git checkout -b branch_name
```
To switch to a desired branch
```
$ git checkout branch_name
```
- Make changes, commit and push it 
```
# To add all the files to branch branch_name
$ git add .

# To commit the changes (This message gets associated with all the files that you have changed)
$ git commit -m 'commit message'

#To push your work to your remote repository
$ git push -u origin branch_name
```
- Open a pull request : The final step 
```
- Go to your repository in browser
- Click on compare and pull requests
- Add a title and description to your pull request
- And its done!
```

## Steps for opening issues
Go to the main page of the repository and click Issues

![alt test](https://help.github.com/assets/images/help/repository/repo-tabs-issues.png)

click new issue

![alt test](https://help.github.com/assets/images/help/issues/new_issues_button.png)

Select your type of issue and click on ```get started```

![alt test](https://help.github.com/assets/images/help/issues/issue_template_get_started_button.png)

Type a title and description for your issue and click on **Submit new issue** and you are done !

