# Pull Request Conflicts

Sometimes, just sometimes, your PR is not in-sync with the latest in master.. and you cannot merge a PR you made in the great github web interface. It happens to the best of us.

Github just says: Merge it manually haha! 

Then you'll be like: `¯\_(ツ)_/¯`. 

Note: You'll see a weird message in github that says you need to pull your latest commits, checkout a
new branch, then do X, Y and Z and still you get no green button, so you just give up and close the
commit and file a new one instead.

However it doesn't really look good to me, because you have to close a PR and then you would have add
a comment saying "I'm sorry guys and gals. I made a mistake, look for a newer PR from this branch here, tihee"

[Here](https://github.com/AgileVentures/MetPlus_PETS/wiki/Resolving-Pull-Request-merge-conflicts) is a better me thinks.

So basically just three things:

1. While on the branch that you used to create the PR (in your repo folder...), do a `git pull origin
<master|develop>` while in your feature branch. Update that `<master|develop>` to  either *master* or
*develop* branches, whichever is the one you are merging the PR into.

2. So, there will be conflicts. I assume you know how to fix those conflicts, if not use a mergetool
like
[vimdiff](http://vim.wikia.com/wiki/A_better_Vimdiff_Git_mergetool). You basically just remove the
HEAD lines usually and the `<<<<<` and the `>>>` and the code that doesn't look right. Then make a
commit  which wouuld get you back to a pointer in your tree.

3. Once you've fixed your conflicts , just push that branch up again to your repo and you should see
your Pull Request have a Green button ready for clicking!

### TLDR;

1. Re-clone the master or develop branch. 
2. Git checkout your PR'd feature branch.
3. Do `git merge master`, fix conflicts if ever, then  `git push origin <feature-branch>`

Updated 03/04/2017



