# Periodic unreviewed code triage

The maintainer has a very central position in our proposal for a minimal sustainable research software infrastructure.
While a maintainer is responsible for integrating external contributions, and for releasing new versions of the software, we did not envision this position as someone who actively extends the software with new features.
Having a maintainer for a project makes sure that there is always a point of contact for other developers who want to contribute to the project. This can help to keep the project alive, and ensures that certain software engineering standards such as code review can be followed.

## Issues with the maintainer role

Keeping a project alive can mean different things depending on the software and the expectation of the community.
We tried to minimize the work that needs to be done by the maintainer and moved responsibility to the community that uses the software to help keep it alive, e.g. by providing funding for a limited time to add a specific feature or fix a bug which is of a particular interest for this user.

However, there are issues that threaten the fundamental availability of the software itself, if not fixed.
For example, if the execution environment changes in a backward incompatible way, sometimes only small adjustments to startup scripts or build configuration can fix these issues.
Or if there is a security issue in one of the dependencies that can easily be fixed by just updating to a fully backward compatible patched version.
If a software can't be run on current systems, but only on out-of-date virtual machines or containers with potentially vulnerable operating systems, the actual usability and “aliveness” of a software is under serious threat.
Some issues can be mitigated to a certain degree by carefully choosing the software your project depends on, but some issues just cannot be predicted.
Thus, maintaining a software may also mean fixing these kinds of issues, and therefore the maintainer may actually have to change code.

This leads to a dilemma: if the maintainer themself is changing the code, who is reviewing it for correctness?

## Pool of reviewers

One possible solution to this problem is to have larger developer community with at least two maintainers.
For projects with a small user base, this may not be achievable even if the software is essential for their research.
In research areas like the humanities, funding for developers is typically limited to an active project phase and there is often only funding for a single developer.
We initially thought that student assistants may be able to fill the gap as second maintainers and reviewers, but hiring a student assistant may not be possible for all projects.

An alternative solution is to have Research Software Engineering (*RSE*) teams at an institution, who can contribute as code reviewer-on-demand.
These RSE groups are essentially professionalized and paid communities of maintainers for a whole institution.
Unfortunately, very few organizations do have such RSE teams as pool for reviewers yet.
It is also not an easy task to develop the permanent funding at each institution that is needed for the establishment of an RSE group, and as such RSE groups do therefore not provide a short term solution.
If a pool of code reviewers could be provided on a larger scale and on a volunteer basis, for example as some kind of "Stack Overflow for open source research software code reviewers", this could enhance the situation for smaller projects.
Still, some way of scheduling this resource is needed, and it is not clear who should do the organization and funding of the platform itself.

## Postponing the review with unreviewed code triages

This idea is based on the current funding situation for smaller projects, especially in the humanities, where the presence of only a single maintainer can be guaranteed for the originally funded lifetime of a software project at most, and where there is no institutional pool of reviewers.
It is inspired by the "weekly performance triage" of the Rust compiler,[^rust-triage] where performance regressions for new code in the compiler are not measured and detected for each pull request, but are triaged every week, and the offending pull request is only identified if a regression has been found in any of the changes since the week before.

For critical bug fixes that hinder the execution of the software (but not for new features or non-urgent bug fixes), the single maintainer can author the fix and add a regular pull request, but decide not to request a code review.
In this case, all required and all optional checks of the continuous integration pipeline must execute successfully.
This includes successful test execution, but specifically also static code analysis, where the goal should be to not introduce any new issue and to stay in the acceptable limits of metrics such as test coverage for new code, or maximum line duplication.
Having an advanced static code analysis in the continuous integration pipeline is a strict requirement for this approach.
Once all checks have passed, the maintainer marks the pull request with a special label for unreviewed pull requests and merges it, thus producing a new hotfix release of the software.

To ensure that all fixes are still reviewed at some point in the future, the project should introduce periodic reviews of previously unreviewed changes.
For Hexatomic, we use a quarterly approach.
During triage, a reviewer will look into a special triage log file in the repository to determine which source revision was triaged last.
Next, all pull requests with the "unreviewed" label are merged into a new version control branch which is based on the last triaged commit.
The changes are reviewed and if there are any issues found, they are added to the issue tracker of the project, so that they can be resolved later.
A triage report is added to the log file, and the "unreviewed" label is removed from all triaged pull requests, so that the next reviewer can start from the latest commit at this point of time.
The process itself is documented in our developer/maintainer documentation, so anyone can perform the triage.

An advantage of this approach is that these code audits can bundle several pull requests, and if there is short-term funding for another developer or the possibility to contract an external company or freelancer to perform these audits, someone who did not write the code is reviewing it.
But even if no external developer is available, and instead the original maintainer performs the reviews after some time, we expect that the maintainer is able to find issues in the code which where overlooked the first time when the code was still actively present in their mind.



[^rust-triage]: See <https://blog.mozilla.org/nnethercote/2020/08/05/how-to-speed-up-the-rust-compiler-some-more-in-2020/> for a description of the process.
