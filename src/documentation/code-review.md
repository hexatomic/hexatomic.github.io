# Code Review

Code review is an essential part of our project: Code and documentation changes come in as pull requests, and all pull requests will undergo review.
We are using the tools of the GitHub platform for performing code reviews in public and do not distinguish between
"internal" contributions from core team members and "external" ones.
Having a platform like GitHub allows to discuss code changes, make these discussions transparent to others and also serve as an additional history
of *how* and *why* the code become part of Hexatomic.
Having such a central place for discussions is especially important for teams where the team members might be split between several institutions and can't meet regularly in the same room.
GitHub was chosen as the general platform for hosting the code, issues, and documentation and GitHub code reviews are highly integrated into the platform.
While we are currently using GitHub code reviews for convenience, the same principles and standards for code review could be applied for other platforms/tools like [Gerrit](https://www.gerritcodereview.com/) or [git-appraise](https://github.com/google/git-appraise).

## Objectives

Developer and maintainer resources are scarce and every code review is an additional overhead to the actual implementation.
An objective is, therefore, to *keep the effort for code review proportional* to the development effort.

Code reviews can request changes and it is important that this feedback loop is *not obstructing the development process*.
It must be ensured that there is both enough time for the developer to address the requested changes and that these changes are reviewed quickly.
Also, as longer a pull request is not processed, more conflicts to other developments can occur and features can not be deployed.

## Responsibilities

It must be clear who is responsible to perform code reviews and these responsibilities have to be documented in the maintainer documentation.
In research projects like Hexatomic, we propose that in general, the maintainer has this responsibility.
They can delegate the code reviews to others if appropriate or necessary.
E.g., if the maintainer is submitting a pull request by themselves, another person should responsible for code review.
Delegating code reviews can be helpful to distribute the workload between several persons.

In Hexatomic we have three areas where contributions require code review.

### Project documentation

The project documentation is similar to a formal project report.
We, therefore, argue that ideally, the documentation should be reviewed by the Project Instructors (PIs).
To avoid a “chicken or egg” problem, project maintainers (who are also the researches in the project) can review each other pull requests to bootstrap the initial documentation, e.g. about how code review is performed.

When the project is finished, the project documentation will probably not need any updates.
If an update is still necessary, the maintainers can decide who should review it.

### User, developer and maintainer documentation

The maintainer should suggest a suitable person for a code review of documentation.
This can include other project members and PIs who are not developers but also external users.
We argue that especially user documentation can benefit from a user perspective in the review process.
This means that the documentation updates and the review interface must be usable for informed users.

### Software code

For changes to the actual Hexatomic software, a maintainer is responsible for code review.

## Review schedules

To find a balance between a quick code review feedback loop and a justifiable overhead for the maintainers, we propose
to have weekly dedicated time slots where the maintainers perform the code review.
How much time and when these time slots depend on the work schedule of the actual maintainer.
The time slots should be documented in the `CONTRIBUTING.md` file to make them transparent to external contributors.
An example would be having two time slots of one hour per maintainer at two days in the week with a day in between.
This would allow the contributor to update the pull request with the requested changes and still get a new review in the same week.
Ideally, a pull request with minor remarks could be merged in the same week.

We think it is important to limit the amount of per-week time a maintainer has to invest in code reviews.
This allows calculating man-hours required to maintain a software project and to plan to finance the maintenance.
If too many code reviews are requested at the same time, we propose to triage them first and give them a visible priority.
