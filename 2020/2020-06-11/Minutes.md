# Tango Kernel Follow-up Meeting - 2020/06/11

Held on 2020/06/11 at 15:00 CEST on Zoom.

Participants:  Andrew Goetz, Damien Lacoste, Reynald Bourtembourg (ESRF), Sergi Rubio (ALBA), Anton Joubert (SKA-ZA), 
Wilmer Nilsson (MaxIV), Thomas Braun (byte physics), Geoffrey Mant (STFC)

# Minutes

## Introduction

2 new guests are attending today:
- Wilmer Nilsson is working at MaxIV and has been involved in the gRPC prototype.
- Damien Lacoste is currently mainly working on HDB++

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2020/2020-05-28/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - Kernel developers**: Look at https://github.com/pulls/review-requested and review/merge pending PRs

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - All**: Test [9.3.4-rc4](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc4) release.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the 
TangoSourceDistribution repository.

**Action - Alba**: Add content to known issues section of the documentation to share some known work-around tricks. 
**Info collected. About 10-12 know issues already collected. They will soon be written on the documentation.**.

**Action - Soleil**: Fix last issues with events in JTango and release a new JTango version which will be used in the next Tango Source Distribution release.
**Jtango 9.6.0 has been released but does not seem to solve all the heartbeat events issues**.

**Action - SKA-ZA**: Create an issue in [TangoTickets repository](https://github.com/tango-controls/TangoTickets) to give more details about the idea of using APM and OpenTracing.  
**Done: See https://github.com/tango-controls/TangoTickets/issues/35**

**Action - Byte Physics**: Clarify with Gwenaelle about Java 8 and 11 support in latest JTango version.
Is there anything to be done to get a Java 8 or 11 compatible version from latest 9.6.0 draft release?
**Jtango 9.6.0 is compatible with all java >= 8 with nothing to do on Tango Source Distribution side.**

**Action - STFC/ALBA**: Geoff will send a question on Tango mailing list and/or Tango Kernel mailing list related to the 
DevEncoded usage in PyTango and the expected python types. Sergi will pass the question to his team in ALBA.
**Geoff managed to get DevEncoded working as expected. So it is no longer needed to send any e-mail to the community.**

**Action - ESRF**: Send link to Geoff to give him access to a recent pytango conda package (beta version). 
**Geoff is especially interested in Python 3.7. Link sent by Reynald on 12th June.**

## cppTango News

Thomas released [cppTango 9.3.4-rc6](https://github.com/tango-controls/cppTango/releases/tag/9.3.4-rc6).

### Recent PR merged
Several PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:

#### tango-9-lts (future 9.4)

- Shared/static switching on windows ([cppTango#688](https://github.com/tango-controls/cppTango/pull/688), [cppTango#656](https://github.com/tango-controls/cppTango/issues/656))
- Fix broken install path for the tango idl file on windows ([cppTango#722](https://github.com/tango-controls/cppTango/pull/722))

#### 9.3 backports

- Backport fix for #496 and #361 - event clients lost after dev restart ([cppTango#702](https://github.com/tango-controls/cppTango/pull/702))

### New issues
No new issue reported in cppTango since the previous Tango Kernel teleconf meeting.

### Recent developments
- Michal has worked on [cppTango#703](https://github.com/tango-controls/cppTango/pull/703) and 
[cppTango#698](https://github.com/tango-controls/cppTango/pull/698) which have been approved by Thomas 
- Michal plans to work on [cppTango#704](https://github.com/tango-controls/cppTango/pull/704) during the next 2 weeks.
- Thomas is working on [cppTango#662](https://github.com/tango-controls/cppTango/pull/662) (Automate abi api compliance check)

### PR Merge goals from last meeting
Here is the list of PR which were with the "Ready For Merge" label at the time of the previous teleconf meeting:

- [cppTango#698](https://github.com/tango-controls/cppTango/pull/698) (high priority) - **Missing 1 approval** 
- [cppTango#685](https://github.com/tango-controls/cppTango/pull/685) (external contribution) **Changes requested**
- [cppTango#703](https://github.com/tango-controls/cppTango/pull/703) **Missing 1 approval** 
- [cppTango#574](https://github.com/tango-controls/cppTango/pull/574) **Missing 1 approval**
- [cppTango#564](https://github.com/tango-controls/cppTango/pull/564) **Missing 1 approval**

### PR merge goals for next meeting
Here is the list of opened PR with "Ready for Merge" label: https://github.com/tango-controls/cppTango/pulls?q=is%3Apr+is%3Aopen+label%3A%22Ready+For+Merge%22

We agreed to set as recurrent goal to review carefully and merge (if approved, of course) the PRs having the "Ready for Merge label" set, 
prioritizing the PR having the "High Priority" label and the external contributions.

Here is the list of PR which were with the "Ready For Merge" label at the time of this teleconf meeting:

- [cppTango#698](https://github.com/tango-controls/cppTango/pull/698) (high priority) - **Missing 1 approval**
- [cppTango#685](https://github.com/tango-controls/cppTango/pull/685) (external contribution) - changes requested
- [cppTango#721](https://github.com/tango-controls/cppTango/pull/721) **Missing 1 approval**
- [cppTango#703](https://github.com/tango-controls/cppTango/pull/703) **Missing 1 approval**
- [cppTango#697](https://github.com/tango-controls/cppTango/pull/697)
- [cppTango#574](https://github.com/tango-controls/cppTango/pull/574) **Missing 1 approval**
- [cppTango#564](https://github.com/tango-controls/cppTango/pull/564) **Missing 1 approval**

## JTango News

[JTango release 9.6.0](https://github.com/tango-controls/JTango/releases/tag/untagged-17f14dd473d312ce29d5) has been released.
The issue with the events seems to be still present. ESRF will try to help Gwenaelle in testing, reproducing the issue and 
understanding the origin of the problem.

## PyTango News

Geoff reports that DevEncoded is now working as expected.
He is working on the exception propagation test (Final test of the test server suite).
Geoff will go on with the test client suite.

Anton suggests to Geoff to fix the merging conflicts so Travis could work as expected.

Still some issues with the Windows builds (Pthreads) ([pyango#355](https://github.com/tango-controls/pytango/issues/355)).
Andy suggests to have S2Innovation working on this issue.
There are still some issues with Windows CI on python 3.8.

**Action - SKA-ZA**: Create an issue for the pb with Windows CI in the corresponding github repository.
**Done on 12th June: https://github.com/tango-controls/boost-ci/issues/2**

## Tango Source Distribution

Tango Source Distribution [9.3.4-rc6](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc6) has been released.

**Action - All**: Test [9.3.4-rc6](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc6) release.

A new version will have to be prepared with the latest version of POGO still supporting Java 8 and with a new JTango 
version when the events issue will be fixed.

Thomas said he will test again the Debian packages (9.3.4-rc4). The last time he tested it was not working.

## Conda packages

A recent change in pytango allows to use BOOST_PYTHON_LIB environment variable to work-around the issue with the 
boost_python library name which changed in recent version.  
As suggested by Clemens Weninger in the [pytango-conda-recipes#1](https://github.com/tango-controls/pytango-conda-recipes/pull/1) 
PR, we should use this in the pytango conda recipe.  
Anton said we could then take away the pin on boost version which was forced on boost <= 1.67.  
Conda forge doesn't build packages for Python 3.5 anymore so if we need more recent version of dependencies like 
omniorb we will have to build them ourselves. 

## High priorities issues

PyTango conda packages ([pytango-conda-recipes#1](https://github.com/tango-controls/pytango-conda-recipes/pull/1) ,
[pytango#346](https://github.com/tango-controls/pytango/issues/346))

- appveyor: Add support for automatic uploading of releases to github ([cppTango#602](https://github.com/tango-controls/cppTango/issues/602))
- Safe interworking between read_attribute() and push_event() ([cppTango#698](https://github.com/tango-controls/cppTango/issues/698))

Reynald would like to draw more attention on [cppTango#679](https://github.com/tango-controls/cppTango/issues/679) 
(Event reconnection issue after renaming a device server instance).

## AOB

### HDB++

The next HDB++ teleconference meeting will take place on Friday 26th June at 14:00 CEST.

### Webinar

Here is the feedback from the Tango kernel teleconf members participants about the first Tango webinar held on 10th June 2020.
- It would be nice to have more time for feedback (in a proper Tango meeting, we have time to catch up during the coffee break)
- The Agenda was too Compact?
- About the webjive presentations, it would be nice to have something slower so people can try it at the same time
- The next time we could try with a normal zoom meeting and enforce raising hand option
- About 120 people attended the webinar.

### Kubernetes

SKA is having some issues when deploying several device servers running on different containers in the same pod.
Sometimes, the DeviceProxy does not seem to connect to the correct device.
There is a suspicion that in this situation 2 different device servers might be exported with the same IP address and listening on the same ports?

**Action - SKA-ZA**: Create an issue in TangoTickets for the issue seen in Kubernetes. 

### Running with no db

Anton asked whether we should implement the support for #dbase=no in the TANGO_HOST variable.
Sergi suggested to have a Look at the Util object to know whether -nodb option has been passed.

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

The next Tango kernel teleconf meeting will take place in 2 weeks on Thursday 25th June 2020 at 15:00 CEST.

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

**Action - Soleil**: Fix last issues with events in JTango and release a new JTango version which will be used in the next Tango Source Distribution release.

**Action - SKA-ZA**: Create an issue in TangoTickets for the issue seen in Kubernetes. 

