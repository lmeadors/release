Test
---

This is a test

Release process - new major release
----

Once you're "feature complete", create a branch:

	$ mvn release:branch -DbranchName=1.7

Next, switch to that branch and do the release:

	$ git checkout 1.7
	$ mvn release:prepare release:perform

That's going to ask you 3 questions:

