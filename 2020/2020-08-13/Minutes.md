# Tango Kernel Follow-up Meeting - 2020/08/13

Held on 2020/08/13 at 15:00 CEST on Zoom.

Participants:  Reynald Bourtembourg (ESRF), Anton Joubert (SKA-ZA), Sergi Rubio (ALBA),
Michal Liszcz, Wojciech Kitka (S2Innovation), Thomas Braun (byte physics)

# Minutes

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2020/2020-07-09/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - Kernel developers**: Look at https://github.com/pulls/review-requested and review/merge pending PRs

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - All**: Test [9.3.4-rc6](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc6) release.
**Thomas is currently testing the 9.3.4-rc6 latest experimental Debian package and will check whether the issue related to the DB update is still present.** 

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the 
TangoSourceDistribution repository.

**Action - Alba**: Add content to known issues section of the documentation to share some known work-around tricks.  

**Action - Soleil**: Fix last issues with events in JTango and release a new JTango version which will be used in the next Tango Source Distribution release.
**JTango 9.6.1 has been released on 16/07/2020. The event issues should be fixed in this version. Some problems seem to remain according to Zibi: 
See https://github.com/tango-controls/JTango/issues/90**

**Action - ESRF**: Prepare cpptango 9.4.x conda package based on tango-9-lts branch.
**Some conda cpptango and tango-test conda packages using cppTango tango-9-lts branch have been generated and can be 
downloaded on https://github.com/tango-controls/tango-conda-recipes/actions/runs/164651901**

**Action - ESRF (Andy)**: Create an issue (in TangoTickets) to transmit a more meaningful error message when 
Corba Transient Timeout exception are received.

## Tango Kernel training
A discussion was triggered by Nick Rees (SKA) on tango-controls #kernel slack channel in order to organize a Tango Kernel training:
 
      Hi kernel team - I would like to raise the idea of a kernel training course to:
      1. Give SKA developers a deeper understanding of the kernel code.
      2. Providing extra resources who can contribute to kernel development (starting with patches and minor improvements).

Lorenzo replied:

    Hi @Nick Rees, @Reynald good to hear about this again. 
    I think it is really similar to the proposal I made September 2019 to organize a sort of one-week full immersion kernel training... 
    My original proposal was to involve the old time developers (e.g. Emmanuel and Pascal) before they retire, mainly for the architectural discussions.
    
Nick would like to fix a date soon for this training but we need to agree on the goals of the training and on the 
format/length of the training before to set a date.
Indeed, preparing a full week training would require more time to prepare the course than a full day training.  
With the COVID-19 crisis, it appears it will be difficult to organize a face to face training so it will have to be a virtual event.  
Reynald is suggesting to organize some small webinars (1h, 1h30) on different topics and to record them so they could be 
replayed easily on youtube or equivalent. Small webinars on specific topics should be easier to prepare and it would be 
easier to keep the attention of the audience.  

Michal suggested, as exercise to solve some of the small, simple current issues we have in the Tango kernel source code (renaming functions, fixing typos, ...).
According to him, it would be a very good way to have a first insight into the code and to get to know the structure of the 
current source code. Then, more complex issues solving could be addressed at a later stage.

Anton suggested to start with an overview of the current organization of the source code and to talk about the IDL.

Sergi suggested to clearly define the limits of the Tango Kernel (cppTango, pyTango, JTango).

Thomas suggested to propose a session on debugging tricks (gdb, valgrind, wireshark,...).

Kernel members are invited to continue this discussion on the tango-controls #kernel slack channel.

## cppTango News

### Recent PR merged
PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:

#### tango-9-lts (future 9.4)

- log4tango: Use BUILD_TESTING option ([cppTango#741](https://github.com/tango-controls/cppTango/pull/741))
- Correct PCH compile definitions in Release mode ([cppTango#748](https://github.com/tango-controls/cppTango/pull/748))
- .travis/gcc-latest/Dockerfile: Update to 10.2.0 ([cppTango#745](https://github.com/tango-controls/cppTango/pull/745))

#### 9.3 backports

- Use map for attribute lookup in MultiAttribute::check_associated ([cppTango#738](https://github.com/tango-controls/cppTango/pull/738))
- log4tango: Use BUILD_TESTING option ([cppTango#743](https://github.com/tango-controls/cppTango/pull/743))
- log4tango/src/StringUtil.hh: Fix spelling contructed -> constructed ([cppTango#751](https://github.com/tango-controls/cppTango/pull/751))

### New issues
The following new issues have been created in cppTango since the previous Tango Kernel teleconf meeting:

- Problems when cross compiling for ARM ([cppTango#740](https://github.com/tango-controls/cppTango/issues/740))
- Disallow for event subscription and unsubscription using different device proxies ([cppTango#747](https://github.com/tango-controls/cppTango/issues/747)
According to  Michal, this one is not difficult to solve but will require 
[cppTango#746](https://github.com/tango-controls/cppTango/pull/746) to be merged first.
- Add Tango::Group::set_source(Tango::DevSource ) method ([cppTango#749](https://github.com/tango-controls/cppTango/issues/749))
- DeviceProxy::subscribe_event(Tango::INTERFACE_CHANGE_EVENT,cb_ptr,true) throwing exception when target device server 
is not running ([cppTango#750](https://github.com/tango-controls/cppTango/issues/750))

### Recent developments

Michal has been working mainly on the following Pull Requests since the last meeting:
- Restore event subscriptions after device server rename and restart ([cppTango#737](https://github.com/tango-controls/cppTango/pull/737))
- Function name and line number in logs and exceptions ([cppTango#742](https://github.com/tango-controls/cppTango/pull/742))
- PImpl Attribute classes ([cppTango#744](https://github.com/tango-controls/cppTango/pull/744))
- Event unsubscription from DeviceProxy destructor ([cppTango#746](https://github.com/tango-controls/cppTango/pull/746))  
This one is also fixing an issue reported in pytango. Anton asked whether a backport is possible and needed.  
A backport in 9.3-backports would imply some changes compared to the current solution written for tango-9-lts branch.
The current fix would break the ABI with cppTango 9.3 versions. It has been decided, following Sergi's proposal, to solve 
this issue in the future cppTango 9.4 only for the moment and to document this issue in the Known Issues section of the 
documentation.

Thomas reviewed several PRs.

### PR Merge goals from last meeting
Here is the list of PR which were with the "Ready For Merge" label at the time of the previous teleconf meeting:

- [cppTango#698](https://github.com/tango-controls/cppTango/pull/698) (high priority) - **Missing 1 approval**
- [cppTango#721](https://github.com/tango-controls/cppTango/pull/721) **Missing 1 approval**
- [cppTango#703](https://github.com/tango-controls/cppTango/pull/703) **Missing 1 approval**
- [cppTango#697](https://github.com/tango-controls/cppTango/pull/697)
- [cppTango#574](https://github.com/tango-controls/cppTango/pull/574) **Missing 1 approval**
- [cppTango#724](https://github.com/tango-controls/cppTango/pull/724) **Missing 1 approval**
- [cppTango#704](https://github.com/tango-controls/cppTango/pull/704) **Missing 1 approval**
- [cppTango#729](https://github.com/tango-controls/cppTango/pull/729)
- [cppTango#726](https://github.com/tango-controls/cppTango/pull/726) **Missing 1 approval**

### PR merge goals for next meeting
Here is the list of opened PR with "Ready for Merge" label: https://github.com/tango-controls/cppTango/pulls?q=is%3Apr+is%3Aopen+label%3A%22Ready+For+Merge%22

We agreed to set as recurrent goal to review carefully and merge (if approved, of course) the PRs having the "Ready for Merge label" set, 
prioritizing the PR having the "High Priority" label and the external contributions.

Here is the list of PR which were with the "Ready For Merge" label at the time of this teleconf meeting:

- [cppTango#698](https://github.com/tango-controls/cppTango/pull/698) (high priority) - **Missing 1 approval**
- [cppTango#721](https://github.com/tango-controls/cppTango/pull/721) **Missing 1 approval**
- [cppTango#703](https://github.com/tango-controls/cppTango/pull/703) **Missing 1 approval**
- [cppTango#697](https://github.com/tango-controls/cppTango/pull/697)
- [cppTango#574](https://github.com/tango-controls/cppTango/pull/574) **Missing 1 approval**
- [cppTango#724](https://github.com/tango-controls/cppTango/pull/724) **Missing 1 approval**
- [cppTango#704](https://github.com/tango-controls/cppTango/pull/704) **Missing 1 approval**
- [cppTango#729](https://github.com/tango-controls/cppTango/pull/729)
- [cppTango#726](https://github.com/tango-controls/cppTango/pull/726) **Missing 1 approval**
- [cppTango#746](https://github.com/tango-controls/cppTango/pull/746) **Missing 1 approval**
- [cppTango#744](https://github.com/tango-controls/cppTango/pull/744)
- [cppTango#742](https://github.com/tango-controls/cppTango/pull/742) **Changes requested**
- [cppTango#737](https://github.com/tango-controls/cppTango/pull/737)

## JTango News

JTango 9.6.1 has been released on 16/07/2020. Please refer to https://github.com/tango-controls/JTango/releases for more details.
It is currently installed in operation at the ESRF.  

Zibi seems to be still experiencing some heartbeat errors when using a network alias for TANGO_HOST 
(See [JTango#90](https://github.com/tango-controls/JTango/issues/90))

## PyTango News

Wojciech Kitka is fighting with the Windows build issue. 
He encountered problems with pytest which is forking subprocesses which are not supported on Windows.
He is working on a solution.

Anton reminded that it should be safe to use a PyTango x.y.z version with any cppTango x.y.v version.

Anton mentioned an issue they are observing with some random changes in the timestamps. More investigations will be 
needed before to create an issue.

## Tango Source Distribution

Thomas worked on [TangoSourceDistribution#85](https://github.com/tango-controls/TangoSourceDistribution/pull/85) (merged)) to 
avoid checking database server process presence when executing "tango start" script.
This pull request solved [TangoSourceDistribution#84](https://github.com/tango-controls/TangoSourceDistribution/pull/84) 
Thomas is currently testing 9.3.4-rc6 experimental Debian package and preparing 9.3.4-rc7.

## Conda packages

cpptango 9.4 beta version conda package 
(([tango-conda-recipes#7](https://github.com/tango-controls/tango-conda-recipes/pull/7)). 
Reynald has done some work on that and managed to generate packages using Github workflow.
Please refer to https://github.com/tango-controls/tango-conda-recipes/pull/8 github workflow artifacts.
Anton would like to get this conda package on a conda channel. He proposed to Reynald to upload it on his personal conda 
channel (Reyn4ld).
It has to be noted that this package is built based on tango-9-lts cppTango branch which is the cppTango 9.4 
development branch (so a moving target), so if this package is built at different times, it might use different versions 
of the tango-9-lts cppTango branch.

Sergi proposed to contact Carlos Pascal to get some advices on how to organize the git repositories where the conda 
recipes are archived/developed.

## High priorities issues

Sergi mentioned there are some issues with Sardana and latest cppTango 9.3.4 version on some beamlines.  
This is the high priority for ALBA.  
The Sardana test suite is passing successfully though with latest cppTango 9.3.4.  
ALBA will create an issue if needed if they manage to prove the issue comes from cppTango 9.3.4.

No new high priority issue reported since the last meeting.
Here are the high priority issues defined during the previous meeting:

On PyTango, the priority is on the Windows build (and tests passing on Windows).

The others priorities are: 

- Conda package with support for Python3.8 [pytango#346](https://github.com/tango-controls/pytango/issues/346))
- Safe interworking between read_attribute() and push_event() ([cppTango#698](https://github.com/tango-controls/cppTango/issues/698))
- Event subscription lost when destroying different DeviceProxy instance ([pytango#372](https://github.com/tango-controls/pytango/issues/372))
- Exception on unsubscription when a client has two proxies for the same attribute ([cppTango#353](https://github.com/tango-controls/cppTango/issues/353))

## AOB

This was not mentioned during the teleconf meeting but a new TangoTickets issue has been created:
- Concurrently executing a command and pushing event leads to dead lock [TangoTickets#39](https://github.com/tango-controls/TangoTickets/issues/39)

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

The next Tango kernel Teleconf meeting will take place on Thursday 28th August 2020 at 15:00 CEST.

## Summary of remaining actions

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - Kernel developers**: Look at https://github.com/pulls/review-requested and review/merge pending PRs

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - All**: Test [9.3.4-rc6](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc6) release.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the 
TangoSourceDistribution repository.

**Action - Alba**: Add content to known issues section of the documentation to share some known work-around tricks.  

**Action - Soleil**: Fix last issues with events in JTango and release a new JTango version which will be used in the 
next Tango Source Distribution release.

**Action - ESRF**: Prepare cpptango 9.4.x conda package based on tango-9-lts branch and upload it to Reyn4ld conda channel 
to ease testing by Anton.

**Action - ESRF (Andy)**: Create an issue (in TangoTickets) to transmit a more meaningful error message when 
Corba Transient Timeout exception are received.