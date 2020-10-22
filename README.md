# git
<h2>collection of useful git command</h2>

<h2>Revert the full commit</h2>
Sometimes you may want to undo a whole commit with all changes. Instead of going through all the changes manually, you can simply tell git to revert a commit, which does not even have to be the last one. Reverting a commit means to create a new commit that undoes all changes that were made in the bad commit. Just like above, the bad commit remains there, but it no longer affects the the current master and any future commits on top of it.<br>


<pre>git revert {commit_id}'</pre>

<h2>About History Rewriting</h2>

Delete the last commit
Deleting the last commit is the easiest case. Let's say we have a remote origin with branch master that currently points to commit dd61ab32. We want to remove the top commit. Translated to git terminology, we want to force the master branch of the origin remote repository to the parent of dd61ab32:

<pre>git push origin +dd61ab32^:master</pre>

<h2>git pull new branch locally from server</h2>
You need to create a local branch that tracks a remote branch. The following command will create a local branch named daves_branch, tracking the remote branch origin/daves_branch. When you push your changes the remote branch will be updated.

<pre>git checkout --track origin/newsletter</pre>

error like this:

<pre>opt/lampp/bin/mysql.server: 264: kill: No such process</pre>

sollution: 

I have seen same problem. Firstly i used these commands:
<pre>
sudo chmod -R 777 /opt/lampp
sudo chown -hR nobody /opt/lampp
sudo chmod -R 755 /opt/lampp
</pre>

Then;
<pre>
sudo service mysql stop
</pre>

So, you should restart the lampp:

<pre>sudo /opt/lampp/lampp restart</pre>

Temporarily switch to a different commit
If you want to temporarily go back to it, fool around, then come back to where you are, all you have to do is check out the desired commit:

# This will detach your HEAD, that is, leave you with no branch checked out:
<pre>git checkout 0d1d7fc32 </pre>
Or if you want to make commits while you're there, go ahead and make a new branch while you're at it:

<pre>git checkout -b old-state 0d1d7fc32</pre>
To go back to where you were, just check out the branch you were on again. (If you've made changes, as always when switching branches, you'll have to deal with them as appropriate. You could reset to throw them away; you could stash, checkout, stash pop to take them with you; you could commit them to a branch there if you want a branch there.)

Hard delete unpublished commits
If, on the other hand, you want to really get rid of everything you've done since then, there are two possibilities. One, if you haven't published any of these commits, simply reset:

# This will destroy any local modifications.
# Don't do it if you have uncommitted work you want to keep.
<pre>git reset --hard 0d1d7fc32</pre>

<pre>
# Alternatively, if there's work to keep:
git stash
git reset --hard 0d1d7fc32
git stash pop
# This saves the modifications, then reapplies that patch after resetting.
# You could get merge conflicts, if you've modified things which were
# changed since the commit you reset to.
</pre>

# You can use git cherry-pick to apply a single commit by itself to your current branch.

Example:<pre> git cherry-pick d42c389f</pre>

# To hard reset a single file to HEAD:

<pre>git checkout @ -- myfile.ext</pre>

# Rename a local and remote branch in git

1. Rename your local branch.
If you are on the branch you want to rename:
<pre>git branch -m new-name</pre>

If you are on a different branch:
<pre>git branch -m old-name new-name</pre>
2. Delete the old-name remote branch and push the new-name local branch.

<pre>git push origin :old-name new-name</pre>
3. Reset the upstream branch for the new-name local branch.
Switch to the branch and then:

<pre>git push origin -u new-name</pre>

You can request a list of all remote repositories that are currently connected to your local repository:

$ git remote -v
  origin  https://test@github.com/test/example.git (fetch)
  origin  https://test@github.com/test/example.git (push)
Use the "add" parameter if you want to connect a new remote repository, in this example named "production":

$ git remote add production https://test@github.com/test/example.git
