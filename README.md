#### Albert is a collection of commands to make it easier to work with several repos

It's tailor-made for MacOS at the moment, it won't work on other operating systems.

**Assumptions made by Albert:** ```brew``` and ```git``` are already installed.

## Setup
- Setup script must be executed as shown below.
- It installs necessary tools, add some configuration to .bash_profile and sets up github team id which is needed for all operations.
- **OPEN A NEW TERMINAL AFTER SETUP IS DONE**, so that changes to .bash_profile/.bashrc/.zshrc are loaded.
- It also asks for root directory where you have your git repos.
- **Usage:** ```./setup "github team name"```
- **Example(for [eng ret web team](https://github.com/orgs/AutoScout24/teams/as24-cxp-engagement-retention-web)):** ```./setup "Engagement"```
- **Example(for team FED):** ```./setup "ConMon"```

### Github access token
- You need to create and store a Github access token in ~/.github_token
- Go to https://github.com/settings/tokens to create one.

## Operations
### Help
- Prints all available operations and their usage messages.

### List repos
- Lists all repos owned by the team.
- **Usage:** ```albert list-repos```

### List pull requests
- Lists all open PRs.
- **Usage:** ```albert list-prs```

### Replace text
- Replaces some text and creates a PR. 
- Meta variable REPO can be used for repository name.
- **Usage:** ```albert replace-text [ -s | -y | -d ] file "search_string" "new_text" "commit_message"```
- **Example:** ```albert replace-text Jenkinsfile "as24-fizz-community-library@v0.10.0" "as24-fizz-community-library@v0.10.1" "Update as24-fizz-community-library version"```
- **-s** : Execute 'sbt clean test' for every repo which is changed
- **-y** : Execute 'yarn install && gulp test' for every repo which is changed
- **-d** : Dry run, changes aren't committed
#### Operation workflow
- Albert does the change and shows git diff
- User can review
- User can confirm - If confirmed, albert commits to `wip/albert` branch and opens a PR
- User can skip
- User can reject change and ask for vim to do the change on the fly

### Execute
- Executes given command in all repositories. 
- Meta variable REPO can be used for repository name.
- **Usage:** ```albert execute "bash_code"```
- **Example:** ```albert execute "echo REPO > repo-name.txt"```

### Merge AMI pull requests
- Merges most recent AMI PR and closes other older AMI PRs in all repositories.
- **Usage:** ```albert merge-ami-prs```

### Set team
- Sets or changes github team id which is needed for all operations.
- **Usage:** ```albert set-team "github team name"```
- **Example:** ```albert set-team "ConMon"```

### Clone all repositories
- Clones all repositories owned by the team under configured ROOT folder.
- **Usage:** ```albert clone-all-repos```

### Remove archived repositories
- Removes archived repos from configured ROOT folder.
- **Usage:** ```albert remove-archived-repos```


### Merge pull requests with matching text
- Merges most recent PRs whose title contains the given text and closes other older matching PRs.
- **Usage:** ```albert merge-prs "Bump s24-base"```

### Create label
- Creates the defined label in all repos. It doesn't overwrite if label already exists.
- **Usage:** ```albert create-label label-name "label description" color-code```
- **Example:** ```albert create-label merge "Pull request can be automatically merged" 0e8a16```

### Open PR
- Commits to a given branch name and opens a PR. It doesn't refresh the local repos, so that manual changes can be made externally with other tools/editors.
- **Usage:** ```albert open-pr "branch_name" "commit_message"```
- **Example:** ```albert open-pr "test_branch" "This is a commit message"```
