# Tango Kernel Follow-up Meeting - 2020/09/10

Held on 2020/09/10 at 15:00 CEST on Zoom.

**Participants**:  Gwenaelle Abeille (SOLEIL), Marco Bartolini (SKAO), Reynald Bourtembourg (ESRF),  
Thomas Braun (byte physics), Piotr Goryl, Michal Liszcz (S2Innovation),  
Anton Joubert (SKA-ZA), Lorenzo Pivetta (ELETTRA), Sergi Rubio (ALBA)

# Minutes

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2020/2020-08-13/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - Kernel developers**: Look at https://github.com/pulls/review-requested and review/merge pending PRs

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - All**: Test [9.3.4-rc6](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc6) release.  
**9.3.4-rc7 has been released. Tests should focus on this version now. Alba is already testing this version. 
Sardana test suite is passing.**

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the 
TangoSourceDistribution repository.

**Action - Alba**: Add content to known issues section of the documentation to share some known work-around tricks.  
**Alba is collecting more tips and tricks and will update this documentation section. They discovered a memory leak issue when the notifd is used and TANGO_HOST is 
defined with the network domain name in the tango host name part.**

**Action - Soleil**: Fix last issues with events in JTango and release a new JTango version which will be used in the 
next Tango Source Distribution release. **Gwen is in touch with Pascal and Zibi to try to fix the heartbeat issues when 
using a TANGO HOST with DNS alias. Sergi will take care of the tests on the ALBA side when Zibi will be on leave.**

**Action - ESRF**: Prepare cpptango 9.4.x conda package based on tango-9-lts branch and upload it to Reyn4ld conda channel 
to ease testing by Anton. **To be done at some point so Anton could set up some CI jobs using cppTango 9.4**

**Action - ESRF (Andy)**: Create an issue (in TangoTickets) to transmit a more meaningful error message when 
Corba Transient Timeout exception are received. **To be done**

## Tango Kernel training

The first Tango Kernel training webinar will take place on Monday 26th October at 9:00 am CET. It will last about 90 minutes.
Please refer to the following link to get the corresponding time in the different areas of the world (Thanks, Marco for the link): 
https://www.timeanddate.com/worldclock/meetingdetails.html?year=2020&month=10&day=26&hour=8&min=0&sec=0&p1=302&p2=37&p3=196&p4=31&p5=195&p6=240&p7=56&p8=1038

We'll try to organize 1 webinar per month.

**Action - ESRF**: Organize a zoom meeting with Michal and Thomas to define how to share the work for the Tango Kernel Training.

## Tango RFCs

Please refer to https://github.com/tango-controls/rfc/wiki/Meeting-2020-09-10 to get the latest news.

The current goal is to get RFC-10 specified for the end of september.

## cppTango News

### Recent PR merged
PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:

#### tango-9-lts (future 9.4)

- CMake: Remove references to MSVC < 14 ([cppTango#724](https://github.com/tango-controls/cppTango/pull/724))
- Fix [cppTango#566](https://github.com/tango-controls/cppTango/issues/566) const reference parameters ([cppTango#574](https://github.com/tango-controls/cppTango/pull/574))

#### 9.3 backports

No new PR merged
Thomas reported an issue with Pogo where the splash screen is loading forever. Pascal did not manage to reproduce this issue.
### New issues
The following new issues have been created in cppTango since the previous Tango Kernel teleconf meeting:

- Fix some sonarcloud complaints ([cppTango#756](https://github.com/tango-controls/cppTango/issues/756))
- Add support for omniORB 4.3 ([cppTango#760](https://github.com/tango-controls/cppTango/issues/760))
- Docker Hub TOS changes ([cppTango#761](https://github.com/tango-controls/cppTango/issues/761))  
Thomas said that this does not seem to be a problem in our current situation. We might need to move our docker images on 
Github in the future if the new Docker Hub limits become a real issue.
- Investigate on Tango Monitor lock taken when push_change_event() is invoked and try to remove this limitation if possible ([cppTango#762](https://github.com/tango-controls/cppTango/issues/762))  

### Recent developments

The following PRs have been created since last Tango Kernel teleconf:

- Bugfix/fix abi checking ([cppTango#755](https://github.com/tango-controls/cppTango/issues/755))
- Replace sprintf with snprintf ([cppTango#757](https://github.com/tango-controls/cppTango/issues/757))
- Allow turning shared library building off ([cppTango#758](https://github.com/tango-controls/cppTango/issues/758))
- Cleanup log4tango ([cppTango#759](https://github.com/tango-controls/cppTango/issues/759))
- Allow turning shared library building off ([cppTango#763](https://github.com/tango-controls/cppTango/issues/763))
- Switch to newer cppzmq version ([cppTango#764](https://github.com/tango-controls/cppTango/issues/764))

[cppTango#758](https://github.com/tango-controls/cppTango/issues/758) and [cppTango#763](https://github.com/tango-controls/cppTango/issues/763) 
will imply that both static and shared libraries are no longer built together.  

Thomas has been doing some tests with omniORB 3.0. He discovered and reported a bug in omniORB which has been fixed (bad configuration file provided with omniORB).  
Thomas said it is the right time to report issues on omniORB 3.0 because it is in pre-release period. 

### PR merge goals for next meeting
Here is the list of opened PR with "Ready for Merge" label: https://github.com/tango-controls/cppTango/pulls?q=is%3Apr+is%3Aopen+label%3A%22Ready+For+Merge%22

We agreed to set as recurrent goal to review carefully and merge (if approved, of course) the PRs having the "Ready for Merge label" set, 
prioritizing the PR having the "High Priority" label and the external contributions.

Here is the list of PR which were with the "Ready For Merge" label at the time of this teleconf meeting:

- [cppTango#698](https://github.com/tango-controls/cppTango/pull/698) **(high priority)** - Missing 1 approval
- [cppTango#704](https://github.com/tango-controls/cppTango/pull/704) **(high priority)** - Missing 1 approval
- [cppTango#763](https://github.com/tango-controls/cppTango/pull/763) **(high priority)** - Missing 1 approval
- [cppTango#697](https://github.com/tango-controls/cppTango/pull/697) - Changes requested
- [cppTango#703](https://github.com/tango-controls/cppTango/pull/703) - Missing 1 approval
- [cppTango#729](https://github.com/tango-controls/cppTango/pull/729) - Missing 1 approval
- [cppTango#737](https://github.com/tango-controls/cppTango/pull/737) - Missing 1 approval
- [cppTango#742](https://github.com/tango-controls/cppTango/pull/742) - Missing 1 approval
- [cppTango#744](https://github.com/tango-controls/cppTango/pull/744)
- [cppTango#746](https://github.com/tango-controls/cppTango/pull/746) - Missing 1 approval
- [cppTango#757](https://github.com/tango-controls/cppTango/pull/757)
- [cppTango#758](https://github.com/tango-controls/cppTango/pull/758) - Missing 1 approval
- [cppTango#759](https://github.com/tango-controls/cppTango/pull/759)

### Travis build for arm

NRC, in Canada, is using an ARM build of the TANGO Kernel on a Linux embedded system.
Given the raising interest and number of use cases involving ARM architectures, it would be desirable to start building 
ARM binaries as part of the Continuous Integration process.  
Marco created [cppTango#767](https://github.com/tango-controls/cppTango/pull/767) to track this task.

## JTango News

Some bugs have been fixed in recent JTango releases.  
The latest release is [JTango 9.6.4](https://github.com/tango-controls/JTango/releases/tag/9.6.4).  
The latest draft release is [JTango 9.6.5](https://github.com/tango-controls/JTango/releases/tag/9.6.5).  

Zibi (ALBA) is be still experiencing some heartbeat errors when using a network alias for TANGO_HOST 
(See [JTango#90](https://github.com/tango-controls/JTango/issues/90)).  
Gwen is working on this issue. Sergi will help testing new versions while Zibi will be away.

## PyTango News

Appveyor is now also build for python 3.8 on Windows but there are still issues with the Windows test suite.

Piotr suggested that Wojciech starts working on [pytango#338](https://github.com/tango-controls/pytango/issues/338) 
(Attribute decorators). Sergi will have a look at this issue.  
Anton prefers that Wojciech concentrates on fixing the issues on Windows he is already assigned to. 

## Tango Source Distribution

[TangoSourceDistribution 9.3.4-rc7](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc7) has been released.
This should be the last release candidate before the official 9.3.4 release.

**Action - All**: Test [9.3.4-rc7](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc7) release. 

Frederic Picca prepared a new Debian package. There is still an issue with the DB upgrade but it is on the Debian side.
All the information describing the bug has been reported upstream.

TangoTest version used in the Tango Source Dsitribution will have to be updated in order to use the latest release (3.0 as of today).  

**Action - All**: Please update [TangoSourceDistribution#87](https://github.com/tango-controls/TangoSourceDistribution/issues/87) 
issue if you notice that a package needs to be updated in the TangoSourceDistribution.

Thomas reported an issue with Pogo where the splash screen is loading forever. Pascal did not manage to reproduce this issue.

**Action - Thomas**: Provide a VM which could be used to witness/debug the Pogo issue with the never-ending splash screen.

## Conda packages

Anton suggests to provide at some point a conda package with cppTango tango-9-lts branch to be able to prepare some pytango 
CI builds/tests using the future 9.4 release. This should be done several months before the expected cppTango 9.4 release date. 

## High priorities issues

No new high priority issues have been raised during the meeting by the different institutes.

Thomas suggested to raise the priority of some cppTango PRs targeting the 9.3-backports branch. He will set the "high priority" 
label on these PRs.

Here are the high priority issues defined during the previous meetings and which have not yet been solved:

On PyTango, the priority is on the Windows build (and tests passing on Windows).

The others priorities are: 

- Safe interworking between read_attribute() and push_event() ([cppTango#698](https://github.com/tango-controls/cppTango/issues/698))
- Event subscription lost when destroying different DeviceProxy instance ([pytango#372](https://github.com/tango-controls/pytango/issues/372))
- Exception on unsubscription when a client has two proxies for the same attribute ([cppTango#353](https://github.com/tango-controls/cppTango/issues/353))

## AOB

### Tango Collaboration Meeting

It appears it will not be possible to organize the Tango Collaboration Meeting in Saint Petersburg in November as hoped.   
An alternative virtual event, similar to the one organized in June 2020 will take place in November. 
It might be a bit longer this time (2 days?).     
Virtual events will be organized until the international situation with COVID-19 improves.

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

The next Tango kernel Teleconf meeting will take place on Thursday 24th September 2020 at 15:00 CEST.

## Summary of remaining actions

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - Kernel developers**: Look at https://github.com/pulls/review-requested and review/merge pending PRs

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the 
TangoSourceDistribution repository.

**Action - Alba**: Add content to known issues section of the documentation to share some known work-around tricks.  

**Action - All**: Test [9.3.4-rc7](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc7) release.  

**Action - Soleil - ESRF - ALBA**: Fix last issues with events reported by ALBA in JTango and release a new JTango version which will be used in the 
next Tango Source Distribution release.

**Action - ESRF**: Prepare cpptango 9.4.x conda package based on tango-9-lts branch and upload it to Reyn4ld conda channel 
to ease testing by Anton.

**Action - ESRF (Andy)**: Create an issue (in TangoTickets) to transmit a more meaningful error message when 
Corba Transient Timeout exception are received.

**Action - ESRF**: Organize a zoom meeting with Michal and Thomas to define how to share the work for the Tango Kernel Training.

**Action - All**: Please update [TangoSourceDistribution#87](https://github.com/tango-controls/TangoSourceDistribution/issues/87) 
issue if you notice that a package needs to be updated in the TangoSourceDistribution.

**Action - Thomas**: Provide a VM which could be used to witness/debug the Pogo issue with the never-ending splash screen.
