# Tango Kernel Follow-up Meeting - 2020/01/23

Held on 2020/01/23 at 15:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants:  Reynald Bourtembourg (ESRF), Sergi Rubio, Jairo Moldes (ALBA)
               Lorenzo Pivetta (Elettra), Piotr Goryl, Michal Liszcz (S2Innovation), Thomas Braun (byte physics)

# Minutes

## Tango Source Distribution

- 9.3.4-rc3 is available.

- 9.3.4-rc4 will be released after [cppTango#665](https://github.com/tango-controls/cppTango/pull/665) will have been merged.
It will include the latest version of the 9.3-backports branch and the latest POGO version too ([TangoSourceDistribution#70](https://github.com/tango-controls/TangoSourceDistribution/issues/70)).

- Tango Database DS crash [TangoSourceDistribution#61](https://github.com/tango-controls/TangoSourceDistribution/issues/61): 
The problem was due to a bug in libmariadb2. No problem when using libmariadbclient18 or libmariadb3.

**Action - byte physics**: Display a warning in the summary appearing at the end of _configure_ script execution if libmariadb2 is detected.

## cppTango News

### Recent PR merged
Several PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:
- Require C++ 11 and CMake 3.7 [cppTango#653](https://github.com/tango-controls/cppTango/pull/653)
- Reset Database and DS for each test [cppTango#640](https://github.com/tango-controls/cppTango/pull/640)
- Only install PTHREAD_WIN_FILES if it is enabled [cppTango#644](https://github.com/tango-controls/cppTango/pull/644)
- Fix snprintf detection [cppTango#650](https://github.com/tango-controls/cppTango/pull/650)
- Travis: Add testing with Ubuntu 20.04 a.k.a focal [cppTango#652](https://github.com/tango-controls/cppTango/pull/652)

### Ongoing tests

Michal has been working on [cppTango#511](https://github.com/tango-controls/cppTango/issues/511).
He proposed [cppTango#641](https://github.com/tango-controls/cppTango/pull/641) to fix the issue.
The patch is currently under test at the ESRF. No crash so far since 2 days (it was crashing several times a day without the patch).
The device server under test used to crash several times a day before this patch.

Elettra is currently testing the patch too on PowerPC since several hours without any crash.
With the previous version, it used to crash every ~10 minutes.

Alba has encountered this bug too but they disabled the polling as a work-around because they could live without polling in their use case.

It has been decided to backport this patch into 9.3-backports branch and to wait for its merge before releasing the 
Tango Source Distribution 9.3.4-rc4. To be followed on [cppTango#665](https://github.com/tango-controls/cppTango/pull/665).

### Ongoing developments

Michal said there are some PRs where he would need some input. Reynald suggested to add the question label to these PRs and to list these PRs here.

[Michal] Following issues need comments from developers and/or users:
* [cppTango#416](https://github.com/tango-controls/cppTango/issues/416): Remote vs local transparency difference when reading spectrum or image attributes
* [cppTango#401](https://github.com/tango-controls/cppTango/issues/401): Cannot change alarm range for memorized attribute
* [cppTango#538](https://github.com/tango-controls/cppTango/issues/538): Cannot poll local dynamic command

Thomas is currently working on a automatic ABI compliance checker which would inform us if a PR is breaking the API or API compatibility.
He is also preparing some PRs to do some additional C++ 11 cleanup.

### Boost libraries in cppTango
Question raised in [cppTango#648](https://github.com/tango-controls/cppTango/issues/648): Possibility to use boost libraries?

Please do not hesitate to share your opinion and experience on [cppTango#648](https://github.com/tango-controls/cppTango/issues/648) issue.

Michal reminded the participants that he would like to eventually use some Boost features which are header-only and already part of the latest C++ standards (part of c++14, c++17 or c++20).
He does not want to use Boost features which are not in the latest C++ standards.

Michal said we should study the possibility to reorganise the headers into public/private headers in cppTango before taking this decision.

## JTango News

Gwenaëlle worked on improving the events system in JTango (similar work as what was done in cppTango 9.3).
Some tests have been done at the ESRF. Some issues have been reported and will be fixed.

## PyTango News

Sergi said they would be interested in testing pybind11 development version to compare with the current version.
Reynald mentioned that he could have a look at the [pybind11 branch in pytango github repository](https://github.com/tango-controls/pytango/tree/pybind11).

## High priorities issues

## AOB

### Tango meetings in Russia

This topic was not addressed since Igor/Olga & Andy could not attend this meeting.

**Igor**: registration for the meeting is now open! Please proceed to the event's Indico page for more information: [link](https://indico.esrf.fr/indico/event/41/)

### Conda packages

The latest available tango conda package is providing cppTango 9.3.2.
Some known critical bugs have been fixed in cppTango 9.3.3 and 9.3.4-rc versions. It would be good to prepare a new more recent tango conda package.

**Action - ESRF**: Contact Tiago to get information on how to create a new official tango-controls conda package and find a way to automate/simplify this process.   

### TangoTest improvements 

TangoTest repositories has currently 2 issues opened and no one seems to feel responsible for this TangoTest GitHub repository.
https://github.com/tango-controls/TangoTest/issues

Piotr will check whether S2Innovation could provide some resources to work on this.

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET (Paris time).

The next Tango kernel teleconf meeting will take place **in 3 weeks** on Thursday 13th February 2020 at 15:00 CET.

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2020-01-09/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - Thomas Braun**: Test 9.3.4-rc2 packages from Ping Frédéric Picca, provide feedback, ask to create new packages 
for rc4 (rc3 plus new cppTango plus X). **Thomas created [TangoSourceDistribution#67](https://github.com/tango-controls/TangoSourceDistribution/issues/67) to follow the issues he found.**

**Action - All**: Test [9.3.4-rc3](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc3) release.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the 
TangoSourceDistribution repository.

**Action - S2Innovation**: Piotr said he will take care of the documentation issues reported while preparing this 9.3.4 
Tango source distribution release. **Piotr created new issues in tango-doc repository to keep track of these issues reported.**
Piotr will also update the Tango documentation to add links to rpm files created/used by Max IV. 
**Piotr created [tango-doc#310](https://github.com/tango-controls/tango-doc/issues/310)**

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could
use tango-controls.

**Action - Soleil**: Implement the fix for events with network aliases. **WIP**

**Action - Elettra**: Tests on PR [cppTango#641](https://github.com/tango-controls/cppTango/pull/641) are welcome. **Under tests**.

**Action - Nexeya**: Review [cppTango#642](https://github.com/tango-controls/cppTango/pull/642) and 
[cppTango#644](https://github.com/tango-controls/cppTango/pull/644). **PRs Approved by Sebastien Gara** 

**Action - All**: Agree on where to create a wiki page to list the OS/Compilers used to run Tango in the different institutes. 
**Thomas suggested to create a page in the Tango documentation (in tango-doc repository)**

## Summary of remaining actions

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - All**: Test [9.3.4-rc4](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc4) release when it will be out.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the 
TangoSourceDistribution repository.

**Action - S2Innovation**: Piotr said he will take care of the documentation issues reported while preparing this 9.3.4 
Tango source distribution release. 
Piotr will also update the Tango documentation to add links to rpm files created/used by Max IV.

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could
use tango-controls.

**Action - Soleil**: Implement the fix for events with network aliases.

**Action - Nexeya**: Comment [cppTango#656](https://github.com/tango-controls/cppTango/issues/656)

**Action - All**: Create and update page in tango-doc to list the OS/Compilers used to run Tango in the different institutes.

**Action - byte physics**: Display a warning in the summary appearing at the end of _configure_ script execution if libmariadb2 is detected.

**Action - ESRF**: Contact Tiago to get information on how to create a new official tango-controls conda package and find a way to automate/simplify this process.

**Action - S2Innovation?**: Create a page in tango-doc where each institute could list the operating systems where cppTango and PyTango are running in their institutes.
It could probably be interesting to list as well the java versions used for the JTango applications.
