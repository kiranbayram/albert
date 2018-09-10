#### Albert is a script to assist you do simple changes to multiple repos efficiently

```albert set-team finance```
- it asks confirmation if only one matched, lists all with indexes if multiple matches

```albert replace-line [file path] [search string] [new string]```

```albert replace-text [file path] [search string] [new string]```

```albert update-dependency-version [library name] [new version number]```
- For this operation, we can include sbt compile/test to inform user if everything is alright after version update

```albert does the change and shows git diff```
- user can review
- user can confirm - If confirmed, albert commits and pushes it to master branch
- user can skip
- user can reject change and ask for vi to do the change on the fly


#### Extra functions:
- Merge most recent AMI update PRs
- Add/remove a user/team to/from all repos
- Log list repo names which are skipped or rejected by user at the end of execution, so that user can continue with those manually
