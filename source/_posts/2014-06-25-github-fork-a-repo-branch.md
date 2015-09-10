---
layout: post
title:  "github fork a repo branch"
date:   2014-06-26 09:23:50
categories: git

---
[link](http://stackoverflow.com/questions/9227873/fork-from-a-branch-in-github)
I don’t know a native way yet, but you can do it following this recipe:

* Fork the repository in question (called ‘upstream’) on the GitHub website to your workspace there.
* Run the GitHub desktop application and clone the repository onto your PC.
* Use the GitHub desktop application to open a shell in the repository. (The git commands are not available from the default PowerShell unless you configure that manually.)
* Set the source repository as upstream:

		git remote add upstream https://github.com/{user}/{source-repo}.git




* Fetch the full upstream repository. (Right now, you only have a copy of its master branch.)

		git fetch upstream
		
* Make your file system copy the branch you want and give it any name:
		
		git checkout upstream/{branch-in-question}
		git checkout -b temporary
* Publish your repo using the GitHub desktop application.

* On the GitHub website, open your repository and click ‘settings’.
* Change the “Default branch” to ‘temporary’. (Just change the drop-down menu, you don’t need to click the “Rename” button.)
* Go back to your repository, go to the ‘branches’ tab, now you can delete the “master” branch.
* Delete the master branch on your shell and make a new master branch:
		
		git branch -d master
		git branch master
		git checkout master
		git -d temporary
* Once more, publish your repo using the GitHub desktop application.

* On the GitHub website, open your repository and click ‘settings’.
* Change the “Default branch” back to the (new) ‘master’ branch.
* Go back to your repository, go to the ‘branches’ tab, now you can delete the “temporary” branch.


This should be what you were looking for. Perhaps GitHub will provide a more convenient way to do this in future (e.g., clicking “Fork” from a project’s branch results in exactly this behaviour).