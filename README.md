#### Albert is a collection of commands to make it easier to work with several repos

### Setup
- Installs necessary tools and sets up github team id which is needed for all operations.
- **Usage:** ```./albert setup "github_team_name"```
- **Example:** ```./albert setup "ConMon"```

### List repos
- Lists all repos owned by the team
- **Usage:** ```./albert list-repos```

### Replace text
- Replaces some text and pushes that to master if requested in all repositories. 
- Meta variable REPO can be used for repository name.
- **Usage:** ```./albert replace-text [ -s | -y ] file "search_string" "new_text" "commit_message"```
- **Example:** ```./albert replace-text Jenkinsfile "input 'Continue?'" "timeout(time: 1, unit: 'HOURS') { input 'Continue?' }" "Add timeout for Jenkins approval stages"```
- **-s** : Execute 'sbt clean test' for every repo which is changed
- **-y** : Execute 'yarn install && gulp test' for every repo which is changed
#### Operation workflow
- Albert does the change and shows git diff
- User can review
- User can confirm - If confirmed, albert commits and pushes it to master branch
- User can skip
- User can reject change and ask for vim to do the change on the fly

### Execute
- Executes given command in all repositories. 
- Meta variable REPO can be used for repository name.
- **Usage:** ```./albert execute "bash_code"```
- **Example:** ```./albert execute "echo REPO > repo-name.txt"```

### Merge AMI pull requests
- Merges most recent AMI pull requests
- **Usage:** ```./albert merge-ami-prs```

### Set team
- Sets up github team id which is needed for all operations.
- **Usage:** ```./albert set-team "github_team_name"```
- **Example:** ```./albert set-team "ConMon"```


### Clone all repositories
- Clones all repositories owned by the team under ~/git folder
- **Usage:** ```./albert clone-all-repos```

