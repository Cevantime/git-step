#git step

A simple script that adds the git step command to git. git step will move you forward one commit in the repository. This is intended for use when using code as a teaching teaching or lecturing aid.

For example it is common to write code whilst teaching, sometimes errors are made and this may slow the lecture or confuse students. This can be solved by having all code on slides, but you loose the interactivity that raw code supplies.

###Using git step
- Create a git repository
- Commit every time the next step in the code is written
- Checkout the initial commit
- Run git step to step through

Now we can step through the code much like a slide show, however we can make temporary changes, compile the code and run the code.

###Installation

1. `wget https://github.com/SmileyJames/git-step/git-step -P /usr/bin`
2. `chmod +x /usr/bin/git-step`
3. `git step`

###The Code
```bash
#!/bin/bash -e
git reset --hard
HEAD=$(git rev-parse HEAD)
FORWARD=$(git log --format='%H %P' --all | grep -F " $HEAD" | cut -f1 -d' ')
HASH=$(git describe --always $FORWARD)
git checkout $HASH
```