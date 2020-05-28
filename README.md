# GIT FLOW IMPLEMENTATION
This project aim to test the usecase of having an existing projet where we implement GitFlow.  
Checking if it is possible and to what extend or not.  
NB: currently using a mac so some command such as "touch" are different


* Test: exisiting repository
In order to apply GitFlow in an existing project having git initiated ( no existing code versionning ).  
on the project I choose to get a whole boilerplate including the git initialisation  
using create-react-app boilerplate generating a first commit on a branch master  
	* To Test: existing project with existing version control ( result from "git init")  
		> 	npx create-react-app git-flow-test-existing-branching-model  


	* To Test: how GitFlow handles existing local branch having a similar branch nomination pattern  
	than the the one from gitFlow ( ex: master )  
	Creating a first modification by creating a file + make change ( on master )  
		> touch text.md && nano text.md ( interaction system to write into the file from terminal )  
		> gaa ( git add * alias ) && git commit -m 'Init text.md file'  


	* To Test: how would react GitFlow when the existing project has a similar sub branch nomination pattern  
	( ex: feature/plop )  
	Simulating an existing "develop" branch in order to check how gitFlow handles existing branch using  
	it's branching nomination pattern:  
		* create a branch local develop from master called "develop/plop"
		* create a file to handles versionning differences to stage
		* staging files and commit

		> git checkout master && git checkout -b develop/plop
		> touch plop.txt && nano plop.txt ( add some txt )
		> gaa && git commit -m ' test feature/plop recognization from gitflow'


	* To Test: how GitFlow handles branches with no nomination pattern
		* get back to master and create new branch
		* create a file to handles versionning differences to stage
		* staging files and commit

		> git checkout master && git checkout -b no-nomination-pattern
		> touch randomText.txt
		> gaa && git commit -m 

	* To Test: how GitFlow handles exisiting remote project having those branches
		* set remote repository since we just created this emulating "existing project"
		* push branches to save them on remote repository ( no merge ) [ master, develop/plop && no-nomination-pattern ]
		> git remote add origin https://github.com/LaurelineP/git-flow-test-existing-branching-model.git
		> git push --set-upstream origin master


* GIT FLOW IMPLEMENTATION
	* Installation
	> brew install git-flow

	* Initialisation
	> git flow init

	* Interractive console following git flow init command
		- Which branch should be used for bringing forth production releases?  
			( listing your existing branches )
			- confirm having Branch name for production releases [master]
			> hit enter
		- Which branch should be used for integration of the "next release"? 
			> develop then hit enter
			> ( output ) Branch name for "next release" development: [master] develop
			> ( output ) Local branch 'develop' does not exist.

	- Create branch develop ( from master )
	- Update Git flow
	> git checkout -b develop
	> git flow init

	* Interractive console following git flow init command
		- Branch name for "next release" development: [develop] ( to confirm )
		> hit enter to confirm

		- How to name your supporting branch prefixes? ( due to existing branch feature/plop )
		- Feature branches? [feature/]
		> hit enter to confirm
		- Release branches? [release/]
		> hit enter to confirm
		- Hotfix branches? [hotfix/]
		> hit enter to confirm
		- Support branches? [support/] ( will be used later )
		> hit enter to confirm
		- Version tag prefix?
		> hit enter to confirm

All done!
From now on git flow commands are available to process.
From now 

- git flow feature : command related to all branch for "next release"
	- list : will list all branches starting with feature/
	> ( output ) plop ( as our branch created before installation gitFlow == feature/plop )

	- Create and start a new feature
	> git flow feature start MYFEATURE ( ==> feature/MYFEATURE )

	- Finish feature development
	> git flow feature finish MYFEATURE

	- Push your feature branch and get back to develop
	> git flow feature publish MYFEATURE

	- Pull updates from your feature ( in remote )
	> git flow feature track MYFEATURE

	- Pull updates from a pushed feature ( in remote )
	git flow feature pull origin OTHER-FEATURE  
	> git flow feature track OTHER-FEATURE ( ==> feature/OTHER-FEATURE )

	- Create a release ( always from develop )
	> git flow release start REALEASE ( ==> release/RELEASE )

	- Push the release ( in case some modifications may be needed from colleagues )
	> git flow release publish RELEASE

	- Pull updates from release
	> git flow release track RELEASE

	- Finish the release by merging all modification back to master and develop  
	 ( keeping them up-to-date ) and delete the RELEASE branche
	> git flow release finish RELEASE

	- Create a hotfix from master ( suposely because it is needed to act on an urgen prod bug )
	> git flow hotfix start BUGX ( ==> hotfix/BUGX )

	- Finish up the hotfix which be merged back to master an develop 
	> git flow hotfix finish BUGX