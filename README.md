#### Albert is a collection of commands to make it easier to work with several repos

## Setup
- Setup script must be executed as shown below.
- It installs necessary tools, add some configuration to .bash_profile and sets up github team id which is needed for all operations.
- Open a new terminal after setup is done, so that changes to .bash_profile are loaded.
- **Usage:** ```./setup "github team name"```
- **Example:** ```./setup "ConMon"```

### Github access token
- You need to set environment variable ACCESS_TOKEN to a Github access token or store it in ~/.github_token
- Go to https://github.com/settings/tokens to create one.

## Operations
### Help
- Prints all available operations and their usage messages.

### List repos
- Lists all repos owned by the team.
- **Usage:** ```albert list-repos```

### Replace text
- Replaces some text and pushes that to master if requested in all repositories. 
- Meta variable REPO can be used for repository name.
- **Usage:** ```albert replace-text [ -s | -y | -d ] file "search_string" "new_text" "commit_message"```
- **Example:** ```albert replace-text Jenkinsfile "input 'Continue?'" "timeout(time: 1, unit: 'HOURS') { input 'Continue?' }" "Add timeout for Jenkins approval stages"```
- **-s** : Execute 'sbt clean test' for every repo which is changed
- **-y** : Execute 'yarn install && gulp test' for every repo which is changed
- **-d** : Dry run, changes aren't committed and pushed
#### Operation workflow
- Albert does the change and shows git diff
- User can review
- User can confirm - If confirmed, albert commits and pushes it to master branch
- User can skip
- User can reject change and ask for vim to do the change on the fly

### Execute
- Executes given command in all repositories. 
- Meta variable REPO can be used for repository name.
- **Usage:** ```albert execute "bash_code"```
- **Example:** ```albert execute "echo REPO > repo-name.txt"```

### Merge AMI pull requests
- Merges AMI pull requests in all repositories where such PR exists.
- **Usage:** ```albert merge-ami-prs```

### Set team
- Sets or changes github team id which is needed for all operations.
- **Usage:** ```albert set-team "github team name"```
- **Example:** ```albert set-team "ConMon"```


### Clone all repositories
- Clones all repositories owned by the team under ~/git folder.
- **Usage:** ```albert clone-all-repos```

