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
    git rebase <commitToBeReplaced> --onto origin/master
### For recursively updating new commits to submodules:
    git submodule update --init --recursive
### For adding a git submodule:
    git submodule add URL
    git submodule init
    git submodule update
### Git stash:
    git stash
    git stash -- path1 path2 (or git stash push path1 path2)
    git stash pop
    git stash pop i
    git stash drop
    git stash drop stash@{i} OR git stash drop i
    git stash list
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

---

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
### Copy file from container to host:
    docker cp <containerId>:/path/to/logInContainer

---

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

---

## Useful sbt commands
    scalafmtAll
    test:compile
    clean
    clean;test:compile
    testOnly <testName> (may sometimes need to also give the name of the folder, e.g. testing/testOnly TESTNAME)
    testOnly <testName> -- -z "<substringOfTestName>"
    testOnly *
    testOnly * -- -t substring
    show dynver

---

## Useful Postman/Newman commands
    newman run POSTMAN_COLLECTION --env-var ENV_VAR=VAR_VALUE --env-var --verbose
    newman run POSTMAN_COLLECTION --env-var ENV_VAR=VAR_VALUE --folder "REQUEST_NAME"

---

## Useful Bruno/Bru commands
    bru run --env-var ENV_VAR=VAR_VALUE --insecure

---

## Useful unzip/extract commands (<https://linuxize.com/post/how-to-unzip-gz-file/>)
    gzip -dk FILE.gz
    tar -xvzf FILE.tar.gz
    tar -xvf FILE.tgz
    unzip FILE.zip

---

## Useful Python/Pip commands
### Create venv:
    pyenv virtualenv <version> <nameOfVenv>
### Start venv using pyenv:
    pyenv activate <nameOfVenv>
### Start venv without pyenv:
    source venv/bin/activate
### Run python test:
    python /path/to/test <test_class>.<test_function>

---

## Useful for downloading files from a remote server
### SFTP:
    sftp -i <sshKey> -P <port> <user>@localhost
    get /path/to/log
### SCP:
    scp -i <sshKey> -P <port> <user>@127.0.0.1:/path/to/log .

---

## Useful Bash commands
### Do a case-insensitive recursive grep in current directory:
    grep -ir PATTERN .
### Create a new file:
    touch FILE_NAME
### Copy file to clipboard:
    xclip -sel c < INPUT_FILE
### Enter root environment using user password (<https://superuser.com/a/105369>):
    sudo su -
### Check which user is currently being used:
    whoami
### Change password for current user:
    passwd INSERT_USER
### Retry until success:
    retryUntilSuccess() { $@; while [ $? -ne 0 ]; do sleep 5; $@; done }
    retryUntilSuccess COMMAND
### Compare two files (and show adjacent lines to changes):
    vimdiff -c "set foldlevel=9999" -R FILE1 FILE2
### Create/Update a symlink/softlink (<https://stackoverflow.com/a/1951752>):
    sudo ln -sf /path/to/file /path/to/symlink
### Function you can call to make logging in to AWS easier (assumes AWS config file is set up in $HOME/.aws/config):
    function awslogin() {
      aws sso login --profile <profile>
      aws2-wrap --profile <profile> --generate
    }
