# Periodic unreviewed code triage

The maintainer has a very central position in our proposal for a minimal sustainable research software infrastructure.
While a maintainer is responsible for integrating external contributions and to release new versions of the software, we did not envision this position as someone who actively extends the software with new features.
Having a maintainer for a project ensures there is always a contact to other developers who want to contribute to the project and that can keep the project alive and that certain software engineering standards like code review can be followed.

## Problems with the maintainer role

Keeping a project alive can mean different things depending on the software and the expectation of the community.
We tried to minimize the work that needs to be done by the maintainer and moved responsibility to the community that uses the software to help to keep it alive, e.g. by providing funding for a limited time to add a specific feature or fix a bug which is of a particular interest for this user.

However, there are issues that threaten the fundamental availability of the software in itself if not fixed.
For example, if the execution environment changes in a backward incompatible way, sometimes only small adjustments to startup scripts or build configuration can already fix these issues.
Or if there is a security issue in one of the dependencies that can easily fixed by just updating to a fully backward compatible patched version.
If a software can't be run on current systems, but only on ancient virtual machines or container with the probably vulnerable operating systems, the actual usability and “aliveness” of a software is under serious threat.
Some issues can be mitigated by a certain degree by carefully choosing the software your project depends on, but some things can't be foreseen.
Thus, to maintain a software might also mean to fix these kinds of issues and so the maintainer might actually need to change code.

This leads to a dilemma: if the maintainer themself is changing the code, who is reviewing it for correctness?

## Pool of reviewers

One possible solution to this problem is to have larger developer community with at least two maintainers.
For projects with a small user base, this might not be achievable even if the software is essential for their research.
In research areas like the humanities, funding for developers is typically limited for the project phase and there is often only funding for a single developer.
We initially thought that student assistants might be able to fill the gap as second maintainers and reviewers, but even hiring a student assistant is not possible for all projects.

An alternative solution is to have RSE teams at an institution who can contribute as code reviewer on demand.
This is essentially a professionalized and paid community of maintainers for a whole institution.
Unfortunately, very few organizations do have such RSE teams as pool for reviewers yet.
It is also also not an easy task to develop the permanent funding at each institution and as such this is not a short term solution.
If such a pool could be provided on a larger scale and on a volunteer base, for example as some kind of "Stack Overflow for open source research software code reviewers", this could enhance the situation for smaller projects.
Still, some way of scheduling this resource is needed and it is not clear who should do the organization and funding of the platform itself.

