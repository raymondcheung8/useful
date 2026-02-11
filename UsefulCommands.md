# Useful commands

## Useful Git commands

    git checkout -b NEW_BRANCH
    git push -u origin LOCAL_BRANCH
    git checkout -b BRANCH origin/BRANCH
    git branch -d BRANCH
    git push origin -d BRANCH
    git branch -r
    git init -b master
    git add -A
    git commit -a

### For recursively updating new commits to submodules:
    git submodule update --init --recursive

### For adding a git submodule:
    git submodule add URL
    git submodule init
    git submodule update

### For removing the previous commit:
    git reset HEAD~1

### Removing the previous merge:
    git reset --merge HEAD~1

### For resetting git project to HEAD:
    git restore .

### For unstaging all staged changes:
    git restore --staged .

### For reverting up to a certain commit as one big commit (<https://stackoverflow.com/a/43081965>):
    git revert --no-commit INSERT_COMMIT_HASH..HEAD (or just 'git revert --no-commit INSERT_COMMIT_HASH..')
    git commit
    git push

### For reverting a merge (<https://stackoverflow.com/a/4114122>):
    git revert -m 1 INSERT_MERGE_COMMIT_HASH

### Push without running pipelines on GitLab:
    git push -o ci.skip

### Switch to previous branch:
    git switch - (or 'git checkout -')

### Tag HEAD of current branch and push to repo:
    git tag INSERT_TAG_NAME HEAD (or just 'git tag INSERT_TAG_NAME')
    git push origin tag INSERT_TAG_NAME

### Change the URI for a remote Git repo (<https://stackoverflow.com/a/2432799>):
    git remote -v
    git remote set-url origin INSERT_NEW_GIT_URL

### Change old commit messages (<https://docs.github.com/en/pull-requests/committing-changes-to-your-project/creating-and-editing-commits/changing-a-commit-message>):
    git rebase -i INSERT_MERGE_COMMIT_HASH (or 'git rebase -i HEAD~n' where n is how many commits back you want to go)
    (replace pick with reword for any commit message you want to change)
    (save and quit)
    (change commit message, then save and quit, for each commit you have chosen)
    (force push)


## Useful Docker commands

### Login to a specific registry:
    docker login --username $ARTIFACTORY_USERNAME --password $ARTIFACTORY_PASSWORD $REGISTRY_URL

### Remove all docker containers:
    docker rm -v -f $(docker ps -qa)

### Check docker containers:
    docker ps -a

### Go into a docker container in bash:
    docker exec -it {NAME/CONTAINER_ID} bash

### Update docker images:
    docker-compose pull


## Useful Hbase shell commands

### Open hbase shell in bash:
    hbase shell

### List all tables:
    list

### List all namespaces:
    list_namespace

### Search table for row names that contain a certain substring:
    scan 'INSERT_TABLE_NAME', { FILTER => "RowFilter(=, 'substring:INSERT_ROW_NAME')" }

### Search table by column name:
    scan 'INSERT_TABLE_NAME', { FILTER => "QualifierFilter(=, 'binary:INSERT_COLUMN_NAME')" }

### Search table by row and column name:
    scan 'INSERT_TABLE_NAME', { FILTER => "(RowFilter(=, 'substring:INSERT_ROW_NAME') AND QualifierFilter(=, 'binary:INSERT_COLUMN_NAME'))" }

### Remove all entries from table:
    truncate 'INSERT_TABLE_NAME'


## Useful sbt commands

    scalafmtAll
    test:compile
    clean
    clean;test:compile
    testOnly TESTNAME
    show dynver


## Useful Postman/Newman commands

    newman run POSTMAN_COLLECTION --env-var ENV_VAR=VAR_VALUE --env-var --verbose
    newman run POSTMAN_COLLECTION --env-var ENV_VAR=VAR_VALUE --folder "REQUEST_NAME"


## Useful unzip/extract commands (<https://linuxize.com/post/how-to-unzip-gz-file/>)

    gzip -dk FILE.gz
    tar -xvzf FILE.tar.gz
    tar -xvf FILE.tgz
    unzip FILE.zip


## Useful Bash commands

### Do a case insensitive recursive grep in current directory:
    grep -ir PATTERN .

### Create a new file:
    touch FILE_NAME

### Copy file to clipboard:
    xclip -sel c < INPUT_FILE

### Enter root environment using user password (<https://superuser.com/a/105369>):
    sudo su -

### Change password for current user:
    passwd INSERT_USER

### Retry until success:
    retryUntilSuccess() { $@; while [ $? -ne 0 ]; do sleep 5; $@; done }
    retryUntilSuccess COMMAND

### Compare two files (and show adjacent lines to changes):
    vimdiff -c "set foldlevel=9999" -R FILE1 FILE2

