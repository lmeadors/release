Test
---

This is a test

Release process - new major release
----

Once you're "feature complete", create a branch:

	$ mvn release:branch -DbranchName=1.7

That's going to ask you a question:

	What is the new working copy version for "release"? (com.elm:release) 1.8-SNAPSHOT: : 

That's adequate, so just press enter like a pro.

Next, switch to that branch and do the release:

	$ git checkout 1.7
	$ mvn release:prepare release:perform

That's going to ask you 3 questions:

	What is the release version for "release"? (com.elm:release) 1.7: : 1.7.0
	What is SCM release tag or label for "release"? (com.elm:release) release-1.7.0: : 1.7.0
	What is the new development version for "release"? (com.elm:release) 1.7.1-SNAPSHOT: : 

The first two defaults are wrong, so you have to fix them; the last one is correct.

Next, you need to merge from the new branch to the `develop` branch:

	$ git checkout develop
	$ git merge 1.7

This will bark at you because the `pom.xml` file has been changed in both the new branch and `develop`, so you will 
need to merge that manually. The two things that will conflict are:

- `/project/version` - you'll want the one from develop
- `/project/scm/tag` - you'll want the one that is `<tag>HEAD</tag>` 

Release process - point release (eg, x.y.1 to x.y.2)
----

Similar process
