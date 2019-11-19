# Tango Kernel Follow-up Meeting - 2019/11/15

Held on 2019/11/15 at 15:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants: Reynald Bourtembourg, Andrew Goetz (ESRF), Thomas Braun (Byte Physics), 
Piotr Goryl, Michal Leszko, Michal Liszcz (S2Innovation), Igor Khokhriakov (IK), Lorenzo Pivetta, Graziano Scalamera (Elettra),
Vincent Hardion (Max IV), Sergi Rubio (Alba), Anton Joubert (SKA-ZA)

# Minutes

## Tango Source Distribution

[9.3.4-rc2](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc2) has been released.

Thanks to Frédéric Picca, 9.3.4-rc2 release is now in Debian Experimental.

Thomas Braun volunteered to do the upgrade tests from tango 9.2.5a Debian package to Tango 9.3.4 Debian package when this will be needed.

Anton asked whether this 9.3.4-rc2 release was shipped with the latest version of Pogo. The answer is "not yet".
Thomas Braun created [TangoSourceDistribution#59](https://github.com/tango-controls/TangoSourceDistribution/issues/59) to upgrade all the tools in the source distribution to their latest version.

Thomas Braun asked whether some institutes have developed some systemd files for Tango Database Server, Tango Starter and TangoAccessControl.
Sergi Rubio said Alba developed such files. He will contact the persons in charge at Alba to get more details. 
This topic can now be followed on [TangoSourceDistribution#58](https://github.com/tango-controls/TangoSourceDistribution/issues/58).

Vincent Hardion said MaxIV also developed some Debian packages to be able to install recent Tango versions on old Debian distributions.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the TangoSourceDistribution repository.

**Action - S2Innovation**: Piotr said he will take care of the documentation issues reported while preparing this 9.3.4 Tango source distribution release.
Piotr will also update the Tango documentation to add links to rpm files created/used by Max IV. 

**Action - All**: Test [9.3.4-rc2](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc2) release.

## cppTango News

A new branch 9.3-backports has been created to provide bug fixes and small improvements for the cppTango 9.3 compatible versions.

### Require newer C++ compilers

In the cppTango project we would like to move to C++11/C++14.
For this we would require newer minimum compiler versions.

Max IV is currently still using CentOS 7 which comes with a compiler which is not compatible with C++ 14. 
They plan to move to CentOS 8 in 2020.

It has been agreed during the meeting to require a C++ 11 compatible compiler for the tango-9-lts branch.
A new decision will be taken around August 2020 to decide whether C++ 14 compatible compilers will be required for this branch too. (Info: C++11 support comes with gcc 4.8 - C++14 support comes with gcc 5.0)

Very old compilers will still be supported in the 9.3-backports branch.

### Require newer cmake version. 
As we move to more C++11 features, it would avoid a lot of additional work if we could use a newer cmake
version which has the required checks builtin. 
From reading [[1]] it seems 3.7 would be good already, this was shipped with debian stretch (oldstable).
Older distros can just download/compile a newer cmake version version as we do now for debian wheezy [[2]]. 

It has been decided during the meeting to require CMake >= 3.7 for tango-9-lts branch.

### cppTango next release number

The next version of the Tango C++ library, which will not be binary compatible, will be named 9.4 and the soname will be changed.
This solution was preferred over naming it Tango 10, which would have been confusing for the users, because Tango 10 is supposed to be the 
first version of Tango on the way to replace CORBA.

New Debian package names will have to be used for this version of the C++ library which will not be binary compatible.
A name like _libtango94_ could be used. A similar solution has already been adopted by other projects, as Thomas Braun showed during the meeting.

Some discussions about the cppTango next release number can be seen in [cppTango#593](https://github.com/tango-controls/cppTango/pull/593).

### Stalled Pull Requests

- Question raised in [cppTango#555](https://github.com/tango-controls/cppTango/pull/555) (Fix crash during alarm state evaluation if attribute value is not set).
It has been decided during the meeting to add a warning log in this special case and to not change the state and status.
- Questions raised in [#504](https://github.com/tango-controls/cppTango/pull/504) (PR to fix #368): Pushing events for State and Status with quality factor and timestamp.
We could not talk about this during the meeting. This will be discussed during the next Kernel Teleconf meeting.
- [#620](https://github.com/tango-controls/cppTango/issues/620), [#540](https://github.com/tango-controls/cppTango/issues/540) 
and [#592](https://github.com/tango-controls/cppTango/issues/592) follow-up. Elettra will comment the issues.
- [#551](https://github.com/tango-controls/cppTango/pull/551)) to implement the server_init_hook() feature. Changes were requested during Thomas Braun's review.
- [#480](https://github.com/tango-controls/cppTango/pull/480): DevEnum Support for commands

Reynald Bourtembourg created [cppTango#552](https://github.com/tango-controls/cppTango/pull/552) to fix a bug which could lead 
to a crash when reading a forwarded state attribute. This PR needs to be reviewed too.

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

## JTango News

A critical issue has been observed at the ESRF with some Java GUIs subscribing to a big number of events.
It was observed that the first event subscription ZMQ message(s) could be dropped silently by jeromq (not sent on the network) 
when trying to subscribe to an attribute on a remote device server. This issue occurs after a big number of event subscriptions and 
when subscribing to an attribute of a remote device server which had not been contacted yet by jeromq for this GUI. 
A fix has been found by setting the SendHwm (send High Water Mark) to 0 on the ZMQ sockets used on the subscriber side.
Here is the commit fixing this issue: https://github.com/tango-controls/JTango/commit/b00043a5df6bd6b4bd95e2ce35c92b871f2e99a7

Travis for openjdk 7 failed. This needs to be investigated.

**Action - JTango team**: Investigate openjdk7 install failure on Travis

**Action - JTango team**: Release a new version of JTango and describe better the problem which has been solved, in the release notes.

**Action - TangoSourceDistribution team**: Use this new JTango release in 9.3.4 source distribution release.

## PyTango News

- SKA has done some work better documenting how DeviceTestContext works - will update PyTango docs
- SKA planning more work on improving unit testing in the next 3-month development cycle.  Prefer mocking DeviceProxy instead of Device, as the latter is much harder.
- MultiDeviceTestContext PR in progress (courtesy of Zibi) [#314](https://github.com/tango-controls/pytango/pull/314)
- For Sardana, [#315](https://github.com/tango-controls/pytango/issues/315) "DS hangs when concurrently subscribing to events and destructing DeviceProxy" - is a blocker.
- Plan release in next month or so, to include above, and a few minor changes: missing db methods, packaging issues.
- Geoff Mant is making progresses on the PyBind11 porting.

**Action - S2Innovation**: Michal Liszcz will Zbigniew Reszela about the issue [pytango#292](https://github.com/tango-controls/pytango/pull/292) and see whether [pytango#315](https://github.com/tango-controls/pytango/pull/315) is due to a similar problem. 


## High priorities issues

**Action - All**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would 
like to get solved first.

## AOB

Pogo updates from SKA progressing. 

The next teleconf meeting will take place around end of November. 

**Action - All**: Please provide your availability in this [Framadate](https://framadate.org/JNHcEkDDOWl5lgOF) to help decide on the next meeting date and time.

**Action - All**: Please review the actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section below.

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2019-05-28/Minutes.md#summary-of-remaining-actions)

**Action - Any (Windows) C++ developer willing to help**: Please help us to solve the Windows specific issues. For 
instance, there is a compilation issue on Windows with cppTango #480 (https://github.com/tango-controls/cppTango/pull/480).

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would 
like to get solved first.

**Action - Anyone willing to help**: Igor is welcoming any additional advice/help anyone could have to help debugging 
the JTango random timeouts issue.

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could 
use tango-controls.

**Action - ESRF**: Advertise cppTango 9.3.3 as stable release. 
cppTango 9.3.3 is now flagged as latest release on GitHub.  

**Action - All**: Test cppTango 9.3.3 and provide feedback.

**Action - cppTango developers, Alba**: Review/Test PR on server_init_hook() ([cppTango#498](https://github.com/tango-controls/cppTango/issues/498))

**Action - All**: Users are encouraged to test the [sys-tango-benchmark](https://github.com/tango-controls/sys-tango-benchmark) tools before the next Tango meeting at Hamburg (beginning of June) and to provide feedback.

**Action - All**: Users are encouraged to test [prepare-9.3.3](https://github.com/tango-controls/TangoSourceDistribution/tree/prepare-9.3.3) TangoSourceDistribution branch and to provide feedback.

**Action - All**: Users are encouraged to test latest Waltz version and to provide feedback.

**Action - ESRF, Elettra, Alba, other institutes interested in contributing to HDB++**: Decide how to organize the next HDB++ meeting. To be discussed during the next Tango meeting in Hamburg.
HDB++ meeting took place 18-20 September at ESRF

**Action - All**: Users are encouraged to test the new TangoBox and to provide feedback.

**Action - ESRF**: Test [TangoSourceDistribution#36](https://github.com/tango-controls/TangoSourceDistribution/pull/36) 
Pull Request on old compilers (gcc 4.4).  Pull Request has been merged.

**Action - ESRF**: Reynald Bourtembourg will prepare a file listing the most important changes provided by this new version and 
explaining how to upgrade from a previous version. This will be presented during the Tango meeting too. The presentation was done.
The cppTango 9.3.3 release notes are explaining what's new and the most critical changes.

**Action - Alba**: Provide some slides giving the latest news from PyTango for the Tango meeting

**Action - JTango team**: Provide some slides giving the latest news from JTango for the Tango meeting

**Action - cppTango developers and volunteers**: Review [cppTango#551](https://github.com/tango-controls/cppTango/pull/551), 
[cppTango#555](https://github.com/tango-controls/cppTango/pull/555), [cppTango#552](https://github.com/tango-controls/cppTango/pull/552), 
[cppTango#530](https://github.com/tango-controls/cppTango/pull/530) (_Closed_) and 
[cppTango#526](https://github.com/tango-controls/cppTango/pull/526) (_Merged_) Pull Requests

**Action - Alba**: Give more details about the issue [pytango#273](https://github.com/tango-controls/pytango/pull/273). 
In any case, this can be discussed at the coming Tango meeting.

## Summary of remaining actions

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would 
like to get solved first.

**Action - All**: Test [9.3.4-rc2](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc2) release.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the TangoSourceDistribution repository.

**Action - S2Innovation**: Piotr said he will take care of the documentation issues reported while preparing this 9.3.4 Tango source distribution release.
Piotr will also update the Tango documentation to add links to rpm files created/used by Max IV. 

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - JTango team**: Investigate openjdk7 install failure on Travis

**Action - JTango team**: Release a new version of JTango and describe better the problem which has been solved, in the release notes.

**Action - TangoSourceDistribution team**: Use this new JTango release in 9.3.4 source distribution release.

**Action - All**: Please provide your availability in this [Framadate](https://framadate.org/JNHcEkDDOWl5lgOF) to help decide on the next meeting date and time.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - S2Innovation**: Michal Liszcz will ping Zbigniew Reszela about the issue [pytango#292](https://github.com/tango-controls/pytango/pull/292) and see whether [pytango#315](https://github.com/tango-controls/pytango/pull/315) is due to a similar problem.

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could 
use tango-controls.

**Action - cppTango developers and volunteers**: Review [cppTango#551](https://github.com/tango-controls/cppTango/pull/551), 
[cppTango#555](https://github.com/tango-controls/cppTango/pull/555) and 
[cppTango#552](https://github.com/tango-controls/cppTango/pull/552) Pull Requests
