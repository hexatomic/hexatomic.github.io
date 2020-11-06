# Code Review

Code review is an essential part of our project: Code and documentation changes come in as pull requests, and all pull requests will undergo review.
We are using the tools of the GitHub platform for performing code reviews in public and do not distinguish between
"internal" contributions from core team members and "external" ones.
Having a platform like GitHub allows us to discuss changes, make these discussions transparent to others, and also use the public discussions as an additional history
of *how* and *why* the code has become part of Hexatomic.
Having a central place for discussions is especially important for distributed teams, where team members might be split over several institutions and cannot meet regularly in the same room.
GitHub was chosen as the general platform for hosting the code, issues, and documentation, and GitHub code reviews are an integral part of the platform.
While we are currently using GitHub code reviews for convenience, the same principles and standards for code review could be applied for other platforms/tools like [Gerrit](https://www.gerritcodereview.com/) or [git-appraise](https://github.com/google/git-appraise).

## Objectives

Developer and maintainer resources are scarce and every code review is an additional overhead to the actual implementation.
An objective is, therefore, to *keep the effort for code review proportional* to the development effort.

Code reviews can request changes and it is important that this feedback loop is *not obstructing the development process*.
It must be ensured that there is both enough time for the developer to address the requested changes and that these changes are reviewed quickly.
Also, the longer a pull request is not processed, the more conflicts to other developments can occur, which may lead to features not being deployed in a timely manner.

## Responsibilities

It must be clear who is responsible for performing code reviews, and these responsibilities have to be documented in the maintainer documentation.
In research projects like Hexatomic, we propose that this should be the general responsibility of the maintainer(s).
They can delegate the code reviews to others if appropriate or necessary.
E.g., if the maintainer is submitting a pull request themself, another person should be responsible for code review.
Delegating code reviews can help distribute the workload over several people.

In Hexatomic we have three areas where contributions require code review.

### Project documentation

One of the purposes of the project documentation is to report progress and outcomes of our research, similar to a formal project report. In fact, it is our approach to generate the project report based on the project documentation.
We therefore argue that ideally, the documentation should be reviewed by the principal investigators (PIs).
To avoid a "chicken and egg" problem, project maintainers who are also the researchers in the project can review each other's pull requests to bootstrap the initial documentation, e.g., about how code review is performed.

Once the project is completed, the project documentation will probably not need any updates.
If an update is still necessary, the maintainers can decide who should review it.

### User, developer and maintainer documentation

The maintainer should suggest a suitable person for a review of changes to documentation.
This can include other project members and PIs who are not developers, but also external users.
We argue that especially user documentation can benefit from a user perspective in the review process.
This means that informed users must be enabled to make updates in and add changes to the documentation, and to use the review user interface. In order to achieve this, the code review process and involved technology is documented in the maintainer documentation, to share with reviewers.

### Software code

For changes to the actual Hexatomic software, a maintainer is responsible for code review. They may also enlist additional reviews from others.

## Review schedules

To find the right balance between a quick code review feedback loop, and justifiable overhead for maintainers, we propose
to have weekly dedicated time slots where the maintainers perform the code review.
How much time is allocated, and when exactly these time slots are, depends on the work schedule of the actual maintainer.
The time slots should be documented in the `CONTRIBUTING.md` file to make them transparent to external contributors.
An example would be to have two time slots of one hour each per maintainer, on two different days in the week, with one day in between the review slots.
This would allow the contributor to update the pull request with the requested changes and still get a new review in the same week.
Ideally, a pull request with minor remarks could be merged in the same week it is created.

We think it is important to limit the amount of time per week a maintainer has to invest in code reviews.
This allows the calculation of man-hours required to maintain a software project, and to plan funding of  maintenance work.
If too many code reviews are requested at the same time, we propose to triage them first and give them a visible priority.
