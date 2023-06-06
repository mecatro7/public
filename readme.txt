# initialize an empty Git repository.

git init

# add your Github repository as a remote destination for your local repository.
git remote add origin <repo_name>


++++++++ Issue #1 +++++++++
error: remote origin already exists.

    # check if the remote already exist
    git remote -v

    # remove it 
    git remote rm origin
+++++++++++++++++++++++++++

# stage all files in your local repository for commit.
git add .

# commit all staged files with a message describing the changes made
git commit -m "Initial commit"


# push the local repository to Github
git push -u origin master


++++++++ Issue #2 +++++++++
$ git push -u origin master
remote: Permission to mecatro7/temp.git denied to zephyrus73.
fatal: unable to access ' <repo_name>': The requested URL returned error: 403
+++++++++++++++++++++++++++

git config --global user.name <user>
git config --global user.email <email>
git config --list
git config --get user.name
git config --get user.email


git remote set-url origin "<repo_name>"