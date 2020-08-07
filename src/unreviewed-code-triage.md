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
If a software can't be run on current systems, but only on ancient virtual machines or container with the probably vulnerable operating systems, the actual usability and "aliveness" of a software is under serious threat.
Some of the issues can be mitigated by a certain degree by carefully choosing the software your project depends on, but some things can't be foreseen.