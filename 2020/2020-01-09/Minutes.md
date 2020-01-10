# Tango Kernel Follow-up Meeting - 2020/01/09

Held on 2020/01/09 at 15:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants: Andrew Goetz, Reynald Bourtembourg (ESRF), Piotr Goryl, Michal Liszcz (S2Innovation),
 Thomas Braun (Byte Physics), Geoffrey Mant (STFC), Gwenaëlle Abeillé (Soleil), Sergi Rubio (Alba),
 Lorenzo Pivetta (Elettra) 

# Minutes

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2019-11-26/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - All**: Test [9.3.4-rc2](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc2) release.
Alba did some simple tests and did not find any issue so far. A critical issue has been raised by @Diego91RA: [TangoSourceDistribution#61](https://github.com/tango-controls/TangoSourceDistribution/issues/61)

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the TangoSourceDistribution repository.

**Action - S2Innovation**: Piotr said he will take care of the documentation issues reported while preparing this 9.3.4 Tango source distribution release.
Piotr will also update the Tango documentation to add links to rpm files created/used by Max IV.

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - JTango team**: Investigate openjdk7 install failure on Travis **Done: Removed java7 support from travis**

**Action - ESRF**: Update JTango 9.5.18 release notes to better describe the problem which has been solved. **Done**

**Action - TangoSourceDistribution team**: Use this new JTango release in 9.3.4 source distribution release. **Done. Available in 9.3.4-rc3**

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - S2Innovation**: Michal Liszcz will ping Zbigniew Reszela about the issue [pytango#292](https://github.com/tango-controls/pytango/pull/292) and see whether [pytango#315](https://github.com/tango-controls/pytango/pull/315) is due to a similar problem. 
**Zbigniew has been contacted. Michal could not reproduce the issue with the simple program provided by Zbigniew and with a suggested work-around so he tried to reproduce it with Sardana. He did not manage to reproduce it. He is now waiting for some input from Alba.**

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could
use tango-controls.

**Action - cppTango developers and volunteers**: Review [cppTango#551](https://github.com/tango-controls/cppTango/pull/551),
[cppTango#555](https://github.com/tango-controls/cppTango/pull/555) and
[cppTango#552](https://github.com/tango-controls/cppTango/pull/552) Pull Requests.
**Done. All 3 PRs have been merged**

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - Thomas Braun**: Thomas will prepare a Pull Request documenting the contribution process and merging policy. 
**Done. A PR requires at least 2 approvals and at least 1 approval from Michal Liszcz, Thomas Braun or Reynald Bourtembourg to be allowed to be merged**

**Action - ESRF**: Contact Gwenaëlle to see whether Soleil could implement the fix for events with network aliases. 
**Done. Gwenaëlle said she will work on it this month (January)**. 

**Action - Geoff**: Push the latest developments to [pytango pybind11 branch](https://github.com/tango-controls/pytango/tree/pybind11) on Github tango-controls pytango repository.
**Done**

**Action - cppTango team**: coordinate on slack to decide who will work on [cppTango#511]((https://github.com/tango-controls/cppTango/issues/511)) issue.
**Michal has been working on it and is waiting for comments and review. 
Tests from Elettra on PR [cppTango#641](https://github.com/tango-controls/cppTango/pull/641) are welcome.**

**Action - S2Innovation**: S2Innovation will call for a technical meeting dedicated to these SKA docker images.
The tango kernel developers, some SKA members and S2Innovation (at least) will be invited. 
**The meeting took place in December. SKA docker images will be renamed and available on official tango-controls docker hub.**

**Action - ESRF**: Send a Doodle-like survey to decide on the best weekday and time for regular Tango Kernel meetings.**Done. Tango Kernel meetings will take place on 2nd and 4th Thursday of each month**

## Tango Source Distribution

- New release candidate? **Done, 9.3.4-rc3 is available**
- Tango Database DS crash [TangoSourceDistribution#61](https://github.com/tango-controls/TangoSourceDistribution/issues/61): 
No similar crash experienced by the participants of this teleconf meeting. To be followed on github.

## cppTango News

Many PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:
* Speedup Travis compilation with -j option (#645)
* Do not require "sed" to enhance generated files (#638)
* Fix crash during alarm state evaluation if attribute value is not set (#555, fix #330)
* Respect TANGO_LOG_PATH set in rc files (#575, fix #500)
* Add data_type_to_string method (#579, Fix #510)
* Fix crash when reading a State forwarded attribute (#550)
* Add server_init_hook() method (#551, fix #498)
* Compile with -Og in debug mode (#612)
* Document contributing process (#639)
* Correct interdependent tests (#634)
* Install tango_admin in CI (#633)
* Remove second database instance for tests (#632)
* CMake cleanups (#624)
* Prevent duplicating defines in case they are already set (#643)
* Fix lintian spelling-error-in-binary: occured -< occurred (#646, #647)
* Add warning error testing with clang(#605)

We got some interesting contributions with the goal being to be able to create Conan cppTango package.

**Action - Nexeya**: Review [cppTango#642](https://github.com/tango-controls/cppTango/pull/642) and [cppTango#644](https://github.com/tango-controls/cppTango/pull/644).

Michal has been working on [cppTango#511](https://github.com/tango-controls/cppTango/issues/511).
He proposed [cppTango#641](https://github.com/tango-controls/cppTango/pull/641) to fix the issue.

**Action - Elettra**: Tests on PR [cppTango#641](https://github.com/tango-controls/cppTango/pull/641) are welcome.

Michal also proposed [cppTango#640](https://github.com/tango-controls/cppTango/pull/640) to execute tests in parallel.
The first tests are impressive and allow to run all the tests in less than 2 minutes on powerful computers.

### Boost libraries in cppTango
Question raised in [cppTango#648](https://github.com/tango-controls/cppTango/issues/648): Possibility to use boost libraries?

No decision has been taken yet to give some time for everybody to think a bit more.
Please do not hesitate to share your opinion and experience on [cppTango#648](https://github.com/tango-controls/cppTango/issues/648) issue.

## JTango News

JTango 9.5.19 has been released. 
Gwenaëlle said it was a release needed mainly for Soleil.
This release contains some changes proposed by Igor to be able to compile in java 11. 
This is still WIP and it seems it does not compile yet with Java 11.

## PyTango News

Latest development for PyBind11 support have been pushed on pytango pybind11 branch by Geoff in December.
Geoff is currently doing some work tests with database and AttributeProxy.

## High priorities issues

## AOB

ESRF will move away from Debian and use the next Ubuntu LTS versions.

Andy is suggesting to create a web page listing all the OS/compilers used to run Tango in the different institutes.
This could be a page on tango-controls.org web page.
Reynald suggested to create a wiki page instead to make it easy to update. It has not been decided yet where to create it.

**Action - All**: Agree on where to create a wiki page to list the OS/Compilers used to run Tango in the different institutes. 

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET (Paris time).

The next Tango kernel teleconf meeting will take place on Thursday 23rd January 2020 at 15:00 CET.

## Summary of remaining actions

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - Thomas Braun**: Test 9.3.4-rc2 packages from Ping Frédéric Picca, provide feedback, ask to create new packages 
for rc4 (rc3 plus new cppTango plus X).

**Action - All**: Test [9.3.4-rc3](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc3) release.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the 
TangoSourceDistribution repository.

**Action - S2Innovation**: Piotr said he will take care of the documentation issues reported while preparing this 9.3.4 
Tango source distribution release. 
Piotr will also update the Tango documentation to add links to rpm files created/used by Max IV.

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could
use tango-controls.

**Action - Soleil**: Implement the fix for events with network aliases.

**Action - Elettra**: Tests on PR [cppTango#641](https://github.com/tango-controls/cppTango/pull/641) are welcome.

**Action - Nexeya**: Review [cppTango#642](https://github.com/tango-controls/cppTango/pull/642) and 
[cppTango#644](https://github.com/tango-controls/cppTango/pull/644).

**Action - All**: Agree on where to create a wiki page to list the OS/Compilers used to run Tango in the different institutes.