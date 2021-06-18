
# Table of Contents

1.  [Update Local Fork](#org2e9373a)
    1.  [foo](#org0d7c4e6)



<a id="org2e9373a"></a>

# Update Local Fork

Note this is possible on github directly however it really only works once
since it moves the local fork ahead by one commit. It's cleaner to use the
command line.


<a id="org0d7c4e6"></a>

## foo

1.  foo

Add <span class="underline">upstream</span> repo to your fork.

    $ git remote add upstream https://github.com/owner/repo.git

Now fetch upstream.

    $ git fetch upstream

Checkout the local fork master and merge changes from upstream/master.

    $ git checkout master
    $ git merge upstream/master

Now that this leaves a extra merge commit in the history which you may not want.
Make an exact copy as using rebase.

    $ git checkout master
    $ git rebase upstream/master

And finally push local origin as needed.

    $ git push
