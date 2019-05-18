# git
collection of useful git command

<h1>Revert the full commit</h1>
Sometimes you may want to undo a whole commit with all changes. Instead of going through all the changes manually, you can simply tell git to revert a commit, which does not even have to be the last one. Reverting a commit means to create a new commit that undoes all changes that were made in the bad commit. Just like above, the bad commit remains there, but it no longer affects the the current master and any future commits on top of it.<br>


<pre>git revert {commit_id}'</pre>

<h1>About History Rewriting</h1>

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
