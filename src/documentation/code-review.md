# Code Review

Code review is an essential part of our project and we decided that codes changes in form of a pull request are reviewed.
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