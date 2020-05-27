GIT FLOW IMPLEMENTATION
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


