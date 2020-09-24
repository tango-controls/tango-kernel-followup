# Tango Kernel Follow-up Meeting - 2020/09/24

Held on 2020/09/24 at 15:00 CEST on Zoom.

**Participants**:  Reynald Bourtembourg, Andrew Goetz (ESRF), Thomas Braun (byte physics), Lorenzo Pivetta (ELETTRA), Nick Rees (SKA-O), Sergi Rubio (ALBA)

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

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the 
TangoSourceDistribution repository.

**Action - Alba**: Add content to known issues section of the documentation to share some known work-around tricks.  

**Action - All**: Test [9.3.4-rc7](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc7) release.  
**This release has been tested at Elettra. Some fixes were needed to build on PPC. Thomas did a patch. It has been tested as well at Alba.
Some issues were seen, but mainly when mixing Tango 7 and Tango 9. Alba will report any Tango 9 related issue.**

**Action - Soleil - ESRF - ALBA**: Fix last issues with events reported by ALBA in JTango and release a new JTango version which will be used in the 
next Tango Source Distribution release. **JTango 9.6.6 seems to fix the issue. Sergi was mentioning that several different 
JTango 9.6.6 were released during the testing phase (some of them working and some of them not working). To be clean, 
a new release 9.6.7 should be done.**  

**Action - ESRF**: Prepare cpptango 9.4.x conda package based on tango-9-lts branch and upload it to Reyn4ld conda channel 
to ease testing by Anton.

**Action - ESRF (Andy)**: Create an issue (in TangoTickets) to transmit a more meaningful error message when 
Corba Transient Timeout exception are received.

**Action - ESRF**: Organize a zoom meeting with Michal and Thomas to define how to share the work for the Tango Kernel Training.
**Sergi said that Guifre is also interested in participating in the preparation of the webinar. Reynald will contact him 
to find the best timeslot for the zoom webinar preparation meeting.**

**Action - All**: Please update [TangoSourceDistribution#87](https://github.com/tango-controls/TangoSourceDistribution/issues/87) 
issue if you notice that a package needs to be updated in the TangoSourceDistribution. **Done**

**Action - Thomas**: Provide a VM which could be used to witness/debug the Pogo issue with the never-ending splash screen.

## Tango RFCs

Piotr supplemented his PRs with sequence diagrams and these are ready to review before merging.
He also started digging into Exceptions section.

## cppTango News

### Recent PR merged
PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:

#### tango-9-lts (future 9.4)

- Allow turning shared library building off ([cppTango#758](https://github.com/tango-controls/cppTango/pull/758))

#### 9.3 backports

- Allow turning shared library building off ([cppTango#763](https://github.com/tango-controls/cppTango/pull/763))

### New issues
The following new issues have been created in cppTango since the previous Tango Kernel teleconf meeting:

- log4tango: Fix the check for int64_t ([cppTango#765](https://github.com/tango-controls/cppTango/issues/765))
- ARM build ([cppTango#767](https://github.com/tango-controls/cppTango/issues/767))
- Fix TANGO_LONGXX usage ([cppTango#768](https://github.com/tango-controls/cppTango/issues/768))
- Handle compile warnings on windows better ([cppTango#769](https://github.com/tango-controls/cppTango/issues/769))
- Use quotes around variables in bash scripts when required ([cppTango#771](https://github.com/tango-controls/cppTango/issues/771))
- Cleanup Tests ([cppTango#772](https://github.com/tango-controls/cppTango/issues/772))  

Andy mentioned an issue with timeouts and attribute mutex errors when using pytango with gevent and greenlets.
 
**Action - Reynald**: See with Andy for the issue related to attribute mutex errors.

### Recent developments

The following PRs have been created since last Tango Kernel teleconf:

- Keep source tree clean and use more targets ([cppTango#766](https://github.com/tango-controls/cppTango/pull/766))
- Fix and document windows build ([cppTango#766](https://github.com/tango-controls/cppTango/pull/770))
- cppapi/server/pollthread.cpp: Catch more exceptions ([cppTango#766](https://github.com/tango-controls/cppTango/pull/773))
  
### PR merge goals for next meeting
Here is the list of opened PR with "Ready for Merge" label: https://github.com/tango-controls/cppTango/pulls?q=is%3Apr+is%3Aopen+label%3A%22Ready+For+Merge%22

We agreed to set as recurrent goal to review carefully and merge (if approved, of course) the PRs having the "Ready for Merge label" set, 
prioritizing the PR having the "High Priority" label and the external contributions.

Here is the list of PR which were with the "Ready For Merge" label at the time of this teleconf meeting:

- [cppTango#698](https://github.com/tango-controls/cppTango/pull/698) **(high priority)** - Missing 1 approval
- [cppTango#704](https://github.com/tango-controls/cppTango/pull/704) **(high priority)** - **Approved**
- [cppTango#697](https://github.com/tango-controls/cppTango/pull/697) - Changes requested
- [cppTango#703](https://github.com/tango-controls/cppTango/pull/703) - Missing 1 approval
- [cppTango#729](https://github.com/tango-controls/cppTango/pull/729) - Missing 1 approval
- [cppTango#737](https://github.com/tango-controls/cppTango/pull/737) - Missing 1 approval
- [cppTango#742](https://github.com/tango-controls/cppTango/pull/742) - Missing 1 approval
- [cppTango#744](https://github.com/tango-controls/cppTango/pull/744)
- [cppTango#746](https://github.com/tango-controls/cppTango/pull/746) - Missing 1 approval
- [cppTango#757](https://github.com/tango-controls/cppTango/pull/757)
- [cppTango#759](https://github.com/tango-controls/cppTango/pull/759)
- [cppTango#770](https://github.com/tango-controls/cppTango/pull/770)
- [cppTango#773](https://github.com/tango-controls/cppTango/pull/773)

Thomas merged [cppTango#704](https://github.com/tango-controls/cppTango/pull/704) during the meeting.

## JTango News

The latest release is [JTango 9.6.6](https://github.com/tango-controls/JTango/releases/tag/9.6.6) and seems to fix the heartbeat errors when using a network alias for TANGO_HOST 
(See [JTango#90](https://github.com/tango-controls/JTango/issues/90)).  

Several 9.6.6 versions have been released during the testing phase. To be clean, a 9.6.7 version will be released. 

**Action - Soleil**: Create JTango 9.6.7

The Tango collaboration will pay a developer to work on JTango tasks. If it appears there are not many issues to solve on JTango, this developer 
will work on improving Pogo (another software part the Tango Steering committee agreed to invest in). 
This work on Pogo is especially important because Pascal Verdier, the original Pogo developer will retire soon (February-March 2021). 

**Action - Pascal**: Go through Pogo issues and close the ones which are already solved.

**Action - Sergi**: Check whether the latest Pogo version is fixing an issue he reported.

## PyTango News

An issue has been reported on the Tango forum related to pytango installation on Ubuntu 20.04 LTS.

## Tango Source Distribution

[TangoSourceDistribution 9.3.4-rc7](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc7) is 
the last release candidate before the official 9.3.4 release.  
As soon as JTango 9.6.7 is released, Tango Source Distribution 9.3.4 can be released.

**Action - Thomas**: Update JTango to 9.6.7 in TangoSourceDistribution and release Tango Source Distribution 9.3.4 if the CI is ok. 

**Action - All**: Test [9.3.4-rc7](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc7) release and 9.3.4 when it will be released. 

## High priorities issues

No new high priority issues have been raised during the meeting by the different institutes.

Here are the high priority issues defined during the previous meetings and which have not yet been solved:

On PyTango, the priority is on the Windows build (and tests passing on Windows).   
Investigations on why pytango installation problems on Ubuntu 20.04 LTS (https://www.tango-controls.org/community/forum/post/4391) should be done.

The others priorities are: 

- Safe interworking between read_attribute() and push_event() ([cppTango#698](https://github.com/tango-controls/cppTango/issues/698))
- Event subscription lost when destroying different DeviceProxy instance ([pytango#372](https://github.com/tango-controls/pytango/issues/372))
- Exception on unsubscription when a client has two proxies for the same attribute ([cppTango#353](https://github.com/tango-controls/cppTango/issues/353))

## AOB

### Tango Kernel Webinar

The first Tango Kernel training webinar will take place on Monday 26th October at 9:00 am CET. It will last about 90 minutes.
Please refer to the following link to get the corresponding time in the different areas of the world (Thanks, Marco for the link): 
https://www.timeanddate.com/worldclock/meetingdetails.html?year=2020&month=10&day=26&hour=8&min=0&sec=0&p1=302&p2=37&p3=196&p4=31&p5=195&p6=240&p7=56&p8=1038

We'll try to organize 1 webinar per month.

The first webinar will present an overview of the code and how to contribute.

Sergi mentioned that Guifre would like to participate in the organization of this Tango Kernel training.
Reynald will propose him to join the next Tango Kernel webinar preparation meeting.

### Tango Collaboration Meeting

It appears it will not be possible to organize the Tango Collaboration Meeting in Saint Petersburg in November as hoped.   
An alternative virtual event, similar to the one organized in June 2020 will take place in November. 
It might be a bit longer this time (2 days around 17th-19th November?).  
Virtual events will be organized until the international situation with COVID-19 improves.

### Panic

Sergi will exchange with S2Innovation to have Panic in python3.

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

The next Tango kernel Teleconf meeting will take place on Thursday 8th October 2020 at 15:00 CEST.

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

**Action - All**: Test [9.3.4-rc7](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc7) release and 9.3.4 when it will be released. 

**Action - Soleil**: Create JTango 9.6.7

**Action - ESRF**: Prepare cpptango 9.4.x conda package based on tango-9-lts branch and upload it to Reyn4ld conda channel 
to ease testing by Anton.

**Action - ESRF (Andy)**: Create an issue (in TangoTickets) to transmit a more meaningful error message when 
Corba Transient Timeout exception are received.

**Action - ESRF**: Organize a zoom meeting with Michal, Thomas and Guifre (and other volunteers) to define how to share the work for the Tango Kernel Training.

**Action - Thomas**: Provide a VM which could be used to witness/debug the Pogo issue with the never-ending splash screen.

**Action - Reynald**: See with Andy for the issue related to attribute mutex errors.

**Action - Pascal**: Go through Pogo issues and close the ones which are already solved.

**Action - Sergi**: Check whether the latest Pogo version is fixing an issue he reported.

**Action - Thomas**: Update JTango to 9.6.7 in TangoSourceDistribution and release Tango Source Distribution 9.3.4 if the CI is ok.
