+++
chapter = false
title = "git"
weight = 5
+++


- `find / -name ".git"` to find all gitrepos
- prettyprint the graph: `git log --all --decorate --oneline --graph`
- `git branch <branchname>` to create new branch
- `git branch -a` to list all branches
- `git checkout <branchname>` to checkout existing branch
- `git branch -f <source> <target>` to move a branch. You cannot be on target.
- forward port reachable from remote host: `ssh -L localport:192.168.x.x:remoteport user@domain.tld` 
