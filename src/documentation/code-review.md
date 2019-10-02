# Code Review

Code review is an essential part of our project and we decided that code and documentation changes in form of a pull request are reviewed.
We are using the tools of the GitHub platform for performing code reviews in the public and don't distinguish between
“internal” contributions from core team members and “external” ones.
Having a platform like GitHub allows to discuss code changes, make these discussions transparent to others and also serve as an additional history
of *how* and *why* the code become part of Hexatomic.
Having such a central place for discussions is especially important for teams where the team members might be split between several institutions and can't meet regularly in the same room.
GitHub was chosen as the general platform for hosting the code, issues and documentation and GitHub code reviews are highly integrated into the platform.
While we are currently using GitHub code reviews for convenience, the same principles and standards for code review could be applied for other platforms/tools like [Gerrit](https://www.gerritcodereview.com/) or [git-appraise](https://github.com/google/git-appraise).

## Objectives

Developer and maintainer resources are scarce and every code review is an additional overhead to the actual implementation.
An objective is therefore to *keep the effort for code review proportional* to the development effort.

Code reviews can request changes and it is important that this feedback loop is *not obstructing the development process*.
It must be ensured that there is both enough time for the developer to address the requested changes and that theses changes are reviewed quickly.
Also, as longer as a pull request is not processed, more conflicts to other developments can occur and features can not be deployed.

## Responsibilities

It must be clear who is responsible to perform code reviews and this responsibilities have to be documented in the maintainer documentation.
In research projects like Hexatomic, we propose that in general, the maintainer has this responsibility.
They can delegate the code reviews to others if appropriate or necessary.
E.g., if the maintainer is submitting a pull request by themselves, another person should responsible for code review.

In Hexatomic we have three areas where contributions require code review.

### Project documentation

The project documentation is similar to a formal project report.
We therefore argue that ideally, the documentation should be reviewed by the Project Instructors (PIs).
To avoid a “chicken or egg” problem, project maintainers (who are also the researches in the project) can review each others pull requests to bootstrap the initial documentation, e.g. about how code review is performed.

When the project is finished, the project documentation will probably not need any updates.
If an update is still necessary, the maintainers can decide who should review it.

### User, developer and maintainer documentation

The maintainer should suggest a suitable person for code review of documentation.
This can include other project members and PIS who are not developers but also external users.
We argue that especially user documentation can benefit from a user perspective in the review process.
This means that the documentation updates and the review interface must be usable for informed users.

### Software code

For changes to the actual Hexatomic software, a maintainer is responsible for code review.