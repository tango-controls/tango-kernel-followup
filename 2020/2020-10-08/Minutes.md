# Tango Kernel Follow-up Meeting - 2020/10/08

Held on 2020/10/08 at 15:00 CEST on Zoom.

**Participants**:  Reynald Bourtembourg (ESRF), Thomas Braun (byte physics), 
Piotr Goryl, Krystian Kedron, Wojciech Kitka, Mateusz, Michal Liszcz (S2Innovation),
 Lorenzo Pivetta (ELETTRA), Nick Rees (SKA-O), Sergi Rubio (ALBA)

# Minutes

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2020/2020-09-24/Minutes.md#summary-of-remaining-actions)

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
**Known issues section is created and available since July: https://tango-controls.readthedocs.io/en/latest/development/advanced/known-issues.html  
Alba already contributed and will continue. Other contributions are welcome of course.** 

**Action - All**: Test [9.3.4-rc7](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc7) release and 9.3.4 when it will be released.
**Alba has already 9.3.4-rc7 fully running on 1 beamline without any new issue so far.**   
**Elettra discovered an issue when compiling on Ubuntu 18.04.5 LTS 32 bits**

**Action - Soleil**: Create JTango 9.6.7. **Not needed. JTango 9.6.6 release is the correct one**

**Action - ESRF**: Prepare cpptango 9.4.x conda package based on tango-9-lts branch and upload it to Reyn4ld conda channel 
to ease testing by Anton.

**Action - ESRF (Andy)**: Create an issue (in TangoTickets) to transmit a more meaningful error message when 
Corba Transient Timeout exception are received.

**Action - ESRF**: Organize a zoom meeting with Michal, Thomas and Guifre (and other volunteers) to define how to share the work for the Tango Kernel Training.
**Tango Webinar preparation Zoom meeting took place this Thursday 8th October.**

**Action - Thomas**: Provide a VM which could be used to witness/debug the Pogo issue with the never-ending splash screen. **Thomas is preparing a VM**

**Action - Reynald**: See with Andy for the issue related to attribute mutex errors. 
**The errors were due to a read attribute callback method which was taking too long from time to time, leading to a timeout. Nothing wrong in Tango.**

**Action - Pascal**: Go through Pogo issues and close the ones which are already solved. **Done**

**Action - Sergi**: Check whether the latest Pogo version is fixing an issue he reported. **To be done**

**Action - Thomas**: Update JTango to 9.6.7 in TangoSourceDistribution and release Tango Source Distribution 9.3.4 if the CI is ok. **9.3.4 is out**

## S2Innovation new collaborators

Piotr introduced Krystian Kedron who joined S2Innovation recently. He used to work at Solaris.
He will contribute to JTango and Pogo.  
He also introduced Mateusz who already started to work on PyTango with Wojciech Kitka.

Piotr also mentioned that Łukasz Żytniak, well known in the Tango community since he worked at ALBA, SOLARIS and MAX-IV, is now project manager at S2Innovation.
He will track the orders from the Community to make sure that all S2Innovation does for Tango is delivered inline with expected schedule, deliverable and budget.

## Tango RFCs

Please refer to https://github.com/tango-controls/rfc/wiki/Meeting-2020-10-08

Some reviews are needed to be able to merge all the pending PRs.

## cppTango News

cppTango 9.3.4 released (still pre-release on Github). Waiting for the release notes to advertise it.

### Recent PR merged
PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:

#### tango-9-lts (future 9.4)

- Correct archive periodic event sending after polling restart ([cppTango#704](https://github.com/tango-controls/cppTango/pull/704))

#### 9.3 backports

### New issues
The following new issues have been created in cppTango since the previous Tango Kernel teleconf meeting:

- Backport for [cppTango#704](https://github.com/tango-controls/cppTango/pull/704) (Correct archive periodic event sending after polling restart)
- Handle deprecated warnings with latest libzmq/cppzmq [cppTango#609](https://github.com/tango-controls/cppTango/pull/609)
- Deploy automatically Doxygen documentation to Github pages (#545)

### Recent developments

The following PRs have been created since last Tango Kernel teleconf:

- INSTALL.md: Add missing cmake options ([cppTango#775](https://github.com/tango-controls/cppTango/pull/775))
- Add more classes to documentation ([cppTango#776](https://github.com/tango-controls/cppTango/pull/776))

Travis tests failures on [cppTango#773](https://github.com/tango-controls/cppTango/pull/773) (cppapi/server/pollthread.cpp: Catch more exceptions).

### PR merge goals for next meeting
Here is the list of opened PR with "Ready for Merge" label: https://github.com/tango-controls/cppTango/pulls?q=is%3Apr+is%3Aopen+label%3A%22Ready+For+Merge%22

We agreed to set as recurrent goal to review carefully and merge (if approved, of course) the PRs having the "Ready for Merge label" set, 
prioritizing the PR having the "High Priority" label and the external contributions.

Here is the list of PR which were with the "Ready For Merge" label at the time of this teleconf meeting:

- [cppTango#698](https://github.com/tango-controls/cppTango/pull/698) **(high priority)** - Missing 1 approval
- [cppTango#746](https://github.com/tango-controls/cppTango/pull/746) **(High priority)** - Missing 1 approval - Has conflict
- [cppTango#697](https://github.com/tango-controls/cppTango/pull/697) - Changes requested
- [cppTango#703](https://github.com/tango-controls/cppTango/pull/703) - Missing 1 approval - Has Conflict
- [cppTango#729](https://github.com/tango-controls/cppTango/pull/729) - Missing 1 approval - Has conflicts
- [cppTango#737](https://github.com/tango-controls/cppTango/pull/737) - Missing 1 approval
- [cppTango#742](https://github.com/tango-controls/cppTango/pull/742) - Missing 1 approval
- [cppTango#744](https://github.com/tango-controls/cppTango/pull/744) - Has conflict
- [cppTango#757](https://github.com/tango-controls/cppTango/pull/757)
- [cppTango#759](https://github.com/tango-controls/cppTango/pull/759)
- [cppTango#766](https://github.com/tango-controls/cppTango/pull/766)
- [cppTango#770](https://github.com/tango-controls/cppTango/pull/770)
- [cppTango#773](https://github.com/tango-controls/cppTango/pull/773)

### Improving the Review Process

A discussion took place during the Tango Kernel Webinar preparation meeting to try improving the efficiency of the merging process.  
As it is now, 2 approvals (1 approval from Thomas, Michal or Reynald + another approval) are required to allow a PR to be merged. 
The creator of a PR cannot merge its own PR. As it is now, only Michal, Thomas and Reynald are reviewing PRs. 
This means they need to approve all the PRs they have not created.
Reynald said that for simple PRs, we could tolerate to merge with only 1 approval or for very simple ones 
(typo fix in documentation or in a comment), even without approval.   
Thomas and Michal role has been upgraded to admin on cppTango Github repository so they are now allowed to force-merge a 
PR even if there are less than 2 approvals.  
Sergi volunteered to do some reviews from time to time for simple PRs. 
Thomas suggested to create a new label _EasyToReview_ to help reviewers with less experience with the cppTango code to 
contribute to the review process, and thus helping to speed up the development process.

## JTango News

The latest release is [JTango 9.6.6](https://github.com/tango-controls/JTango/releases/tag/9.6.6) and seems to fix the heartbeat errors when using a network alias for TANGO_HOST 
(See [JTango#90](https://github.com/tango-controls/JTango/issues/90)).  

## PyTango News

Mateusz has now taken over what Wojciech Kitka was doing for the PyTango tests on Windows.  
He has more experience than Wojciech on Windows and will hopefully find a solution.

## Tango Source Distribution

[TangoSourceDistribution 9.3.4](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4) has been 
released and is waiting for nice cppTango release notes before to advertise it to the Tango community. 

**Action - All**: Test [9.3.4](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4) release

## High priorities issues

No new high priority issues have been raised during the meeting by the different institutes.

Here are the high priority issues defined during the previous meetings and which have not yet been solved:

On PyTango, the priority is on the Windows build (and tests passing on Windows).   
Investigations on why pytango installation problems on Ubuntu 20.04 LTS (https://www.tango-controls.org/community/forum/post/4391) should be done.

The others priorities are: 

- Safe interworking between read_attribute() and push_event() ([cppTango#698](https://github.com/tango-controls/cppTango/issues/698))
- Event subscription lost when destroying different DeviceProxy instance ([pytango#372](https://github.com/tango-controls/pytango/issues/372))
- Exception on unsubscription when a client has two proxies for the same attribute 
([cppTango#353](https://github.com/tango-controls/cppTango/issues/353), [cppTango#746](https://github.com/tango-controls/cppTango/pull/746))

## AOB

### Tango Kernel Webinar

The first Tango Kernel training webinar will take place on Monday 26th October at 9:00 am CET. It will last about 90 minutes.
Please refer to the following link to get the corresponding time in the different areas of the world (Thanks, Marco for the link): 
https://www.timeanddate.com/worldclock/meetingdetails.html?year=2020&month=10&day=26&hour=8&min=0&sec=0&p1=302&p2=37&p3=196&p4=31&p5=195&p6=240&p7=56&p8=1038

We'll try to organize 1 webinar per month.

The first webinar will present an overview of the cppTango code and how to contribute. 
The second webinar end of November will also be dedicated to cppTango. 
It was proposed to do a webinar on JTango and/or Pogo mid-december.

### Tango Collaboration Meeting

It appears it will not be possible to organize the Tango Collaboration Meeting in Saint Petersburg in November as hoped.   
An alternative virtual event, similar to the one organized in June 2020 will take place on 17th and 18th November. 

More information on https://indico.esrf.fr/indico/event/49

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

The next Tango kernel Teleconf meeting will take place on Thursday 22nd October 2020 at 15:00 CEST.

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

**Action - All**: Test [9.3.4](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4) release

**Action - ESRF**: Prepare cpptango 9.4.x conda package based on tango-9-lts branch and upload it to Reyn4ld conda channel 
to ease testing by Anton.

**Action - ESRF (Andy)**: Create an issue (in TangoTickets) to transmit a more meaningful error message when 
Corba Transient Timeout exception are received.

**Action - Thomas**: Provide a VM which could be used to witness/debug the Pogo issue with the never-ending splash screen.

**Action - Sergi**: Check whether the latest Pogo version is fixing an issue he reported.
