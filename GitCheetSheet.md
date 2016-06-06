# Git Quick Reference

Create a new branch and check it out.

    git checkout -b feature_branch_name

Push a new branch to the original server.

    git push -u origin feature_branch_name

Pull a remote branch.

    git fetch origin
    git checkout feature_branch_name

Always push default current `git push -u`.

    git config --global push.default current

## Github Pages

Create an orphan gh-pages branch.

    git checkout --orphan gh-pages

Delete all the files from this branch.

    git rm -rf .

Delete left over directories if there are any (Mac).

    rm -r *

Create the index page.

    echo example.com > index.html

Add the file and commit.

    git add .
    git commit -m 'initial page commit'
