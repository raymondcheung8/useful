# Setup for WSL

1. Install Zscaler certificate (if required) ( https://askubuntu.com/questions/645818/how-to-install-certificates-for-command-line/649463#649463 )
2. Setup git using GCM and set name and email ( https://github.com/git-ecosystem/git-credential-manager/blob/release/docs/wsl.md )
3. Setup docker and allow 'no sudo needed' ( https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04 )
4. Install docker-compose and docker login to run images using docker-compose
5. Install nvim and set as default editor in .bashrc ( https://github.com/raymondcheung8/kickstart.nvim )
6. Override /etc/hosts with whatever is needed and make sure it does not regenerate (https://superuser.com/a/1534975)
7. Configure memory limits in WSL by updating .wslconfig file (https://medium.com/@bonguides25/how-to-configure-memory-limits-in-wsl2-bebdc17e1dd9)
8. Install JDK and Scala using coursier (https://get-coursier.io/docs/cli-installation)
9. Configure realm, host, user and password in .sbt/credentials file
10. Install npm and newman for running postman collections
11. Clone repositories
12. Install IntelliJ and fix markdown not showing on WSL (https://stackoverflow.com/a/74535497)
13. Fix mouse not scaling properly on WSL (https://github.com/microsoft/wslg/issues/61#issuecomment-1286453587)
14. Install aws and aws2-wrap for connecting to AWS CLI and SSO (https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html) (https://github.com/linaro-its/aws2-wrap)
15. Setup .ssh and .ssh/config, note: make sure keys are only read-writable to user (https://stackoverflow.com/a/9270753)
16. Use pyenv to install alt python versions as installing it directly makes it hard to manage and uninstall (https://github.com/pyenv/pyenv)
