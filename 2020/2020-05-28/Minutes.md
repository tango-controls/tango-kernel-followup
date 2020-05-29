# Tango Kernel Follow-up Meeting - 2020/05/28

Held on 2020/05/28 at 15:00 CEST on Zoom.

Participants:  Reynald Bourtembourg (ESRF), Sergi Rubio (ALBA), Anton Joubert (SKA-ZA),
               Geoffrey Mant(STFC), Wojtek Kitka, Michal Liszcz (S2Innovation), Thomas Braun (Byte Physics)
               
# Minutes

## General information
Michal introduced Wojtek Kitka who got recently hired by S2Innovation.
His skills are mainly focused on Python development but he also has some experience with C and C++ and Tango since he 
used to work at SOLARIS.
Wojtek (or Wojciech) will work on PyTango development for the Tango-Controls collaboration.
Anton will supervise his work on PyTango (i.e. identify which issues they should work on and review their commits or vice versa).

Message from Andy Goetz:  
We are in the process of placing the order for PyTango support with S2Innovation.  
We have already placed the 2 orders for cppTango support with S2Innovation and Byte Physics.  
We propose to place the order for JTango support in summer.

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2020/2020-23/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - Kernel developers**: Look at https://github.com/pulls/review-requested and review/merge pending PRs

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - All**: Test [9.3.4-rc4](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc4) release.
**SKA is in the process of updating the Tango version used in their Docker base distribution. They will use 9.3.4-rc releases soon.**

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the 
TangoSourceDistribution repository.

**Action - Alba**: Add content to known issues section of the documentation to share some known work-around tricks.

**Action - Byte Physics**: TangoSourceDistribution: Warn the user if Java version > 8 is detected that Pogo is currently supported on Java 8 only.
** It has been decided to impose Java 8 for all the Tango tools in the coming Tango Source Distribution.
A warning is already displayed if the wrong java version is detected.**

**Action - Soleil**: Fix last issues with events in JTango and release a new JTango version which will be used in the next Tango Source Distribution release.
**[JTango 9.6.0](https://github.com/tango-controls/JTango/releases/tag/untagged-17f14dd473d312ce29d5) in draft release**

**Action - ESRF - SKA-ZA**: Prepare and test TangoTest conda package.
**tango-test conda package is now available on tango-controls conda channel (https://anaconda.org/tango-controls/tango-test). 
It is already used by PyTango Travis CI tests**

**Action - SKA-ZA**: Create an issue in [TangoTickets repository](https://github.com/tango-controls/TangoTickets) to give more details about the idea of using APM and OpenTracing.
**Anton will delegate this task to one of his colleagues.**

**Action - ESRF**: Try to get some feedback from Sebastien Gara and Andy Goetz on [pytango#355](https://github.com/tango-controls/pytango/issues/355)
**Andy has been contacted before the meeting. Sebastien Gara has shortly replied on the associated PR.
Anton would like to get more help to fix this issue. He will recontact Sebastien Gara.
Reynald asked Anton to contact him or Andy in case an official request is required for Sebastien to work on this topic.**  

## cppTango News

### Recent PR merged
Several PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:

#### tango-9-lts (future 9.4)

- Fix compilation errors on OpenBSD ([cppTango#706](https://github.com/tango-controls/cppTango/issues/706), [cppTango#711](https://github.com/tango-controls/cppTango/pull/711)).
This PR will not be backported to 9.3-backport branch.

#### 9.3 backports

- Fix nb_endpoints in ZmqEventConsumer::connect_event_channel ([cppTango#716](https://github.com/tango-controls/cppTango/pull/716)))

### New issues

- Prevent including the wrong include file by accident ([cppTango#720](https://github.com/tango-controls/cppTango/pull/720))

### Recent developments
- Michal has reviewed [cppTango#685](https://github.com/tango-controls/cppTango/pull/685) and detected some potential issues.
Some additional work is required on this PR before being able to merge it.
- Michal worked on the [cppTango#697](https://github.com/tango-controls/cppTango/pull/697) 
(ensure location transparency for image and spectrum attributes) and found an issue due to the refactoring.
He proposed a commit to fix this just before the meeting. So this PR should be ready to be reviewed once the tests will pass.
- Thomas reviewed [cppTango#698](https://github.com/tango-controls/cppTango/pull/698) 
(Safe interworking between read_attribute() and push_event()). Michal will address his comments.
- Thomas reviewed [cppTango#703](https://github.com/tango-controls/cppTango/pull/703) 
(Fix #693: pipe events are lost after RestartServer command). Just a strange indentation needs to be fixed.
- Fix nb_endpoints in ZmqEventConsumer::connect_event_channel [forwardport of #721]([cppTango#703](https://github.com/tango-controls/cppTango/pull/721))

### PR Merge goals from last meeting
Here is the list of PR which were with the "Ready For Merge" label at the time of the previous teleconf meeting:

- [cppTango#702](https://github.com/tango-controls/cppTango/pull/702) (high priority)
- [cppTango#698](https://github.com/tango-controls/cppTango/pull/698) (high priority)
- [cppTango#688](https://github.com/tango-controls/cppTango/pull/688) (external contribution)
- [cppTango#685](https://github.com/tango-controls/cppTango/pull/685) (external contribution)
- [cppTango#703](https://github.com/tango-controls/cppTango/pull/703) 
- [cppTango#574](https://github.com/tango-controls/cppTango/pull/574)
- [cppTango#564](https://github.com/tango-controls/cppTango/pull/564)
- [cppTango#715](https://github.com/tango-controls/cppTango/pull/715)
- [cppTango#702](https://github.com/tango-controls/cppTango/pull/702)

**Action - Byte Physics**: Merge [cppTango#688](https://github.com/tango-controls/cppTango/pull/688) 
(squash commits and commit message explaining why msvc stubs got removed).
**Done just after the meeting.**

### PR merge goals for next meeting
Here is the list of opened PR with "Ready for Merge" label: https://github.com/tango-controls/cppTango/pulls?q=is%3Apr+is%3Aopen+label%3A%22Ready+For+Merge%22

We agreed to set as recurrent goal to review carefully and merge (if approved, of course) the PRs having the "Ready for Merge label" set, 
prioritizing the PR having the "High Priority" label and the external contributions.

Here is the list of PR which were with the "Ready For Merge" label at the time of this teleconf meeting:

- [cppTango#698](https://github.com/tango-controls/cppTango/pull/698) (high priority)
- [cppTango#685](https://github.com/tango-controls/cppTango/pull/685) (external contribution)
- [cppTango#703](https://github.com/tango-controls/cppTango/pull/703) 
- [cppTango#574](https://github.com/tango-controls/cppTango/pull/574)
- [cppTango#564](https://github.com/tango-controls/cppTango/pull/564)

## JTango News

[JTango release 9.6.0](https://github.com/tango-controls/JTango/releases/tag/untagged-17f14dd473d312ce29d5) is on his way (draft), 
including the events fix and Java 11 support.

**Action - Byte Physics**: Clarify with Gwenaelle about Java 8 and 11 support in latest JTango version.
Is there anything to be done to get a Java 8 or 11 compatible version from latest 9.6.0 draft release?

## PyTango News

Geoff has been working on getting the tests running for the following features (DevEnum, exception propagation, DevEncoded).

**Action - STFC/ALBA**: Geoff will send a question on Tango mailing list and/or Tango Kernel mailing list related to the 
DevEncoded usage in PyTango and the expected python types. Sergi will pass the question to his team in ALBA.

Alba is experiencing some memory leak when PyTango 9.3.2 (with latest cppTango) applications are receiving DevDouble events.
Did anyone else experienced the same?

**Action - ESRF**: Send link to Geoff to give him access to a recent pytango conda package (beta version)

## Tango Source Distribution

Rest server version updated to 1.22, will be part of coming release 9.3.4-rc5.

New PR: check for working sed ([TangoSourceDistribution#81](https://github.com/tango-controls/TangoSourceDistribution/pull/81))

A discussion took place to know whether we should use request Java 8 or 11 for the coming TangoSourceDistribution.  
Since the next TangoSourceDistribution will provide cppTango 9.3.4 which is still compatible with some old OS and since 
several institutes are still currently using Java 8 for their Java applications, it has been decided to require Java 8 for the 
coming Tango Source Distribution release.
We will probably impose Java 11 or above only when TangoSourceDistribution 9.4 will be released since cppTango 9.4 will 
be already imposing a more recent version of the C++ standard too and as a consequence won't be compatible with some old OS.

The latest POGO version requires Java 8. A branch is ready for Java 11 but no longer compatible with Java 8. 
Sergi says that Pogo is usually executed on computers dedicated for development which can have a recent Java version.
So for Pogo, keeping the compatibility with Java 8 is not critical. 
We should store the latest Java-8 compatible POGO version in a safe location and use Java 11 from now on for next Pogo development iterations.

## Conda packages

Alba would like to get a PyTango Conda package for python 3.5 because their policy is to use the python coming from the OS, not the one from conda.
Since their OS is providing python 3.5, they would like pytango conda package for python 3.5.

## Tango webinar 10th June 2020

A Tango webinar meeting will take place on 10th June 2020.  
The draft agenda is available here: https://indico.esrf.fr/indico/event/48

Reynald proposed to Michal & Thomas to co-present the cppTango presentation (if they are volunteer, not mandatory). 
In any case, a draft presentation should be transmitted to Michal/Thomas/Reynald to get some feedback before the webinar.

## High priorities issues

Message from Andy Goetz: The highest priority is to get the latest version of Tango and 
PyTango into Debian packaging and conda for all platforms.

- appveyor: Add support for automatic uploading of releases to github ([cppTango#602](https://github.com/tango-controls/cppTango/issues/602))
- Backport fix for #496 and #361 - event clients lost after dev restart ([cppTango#702](https://github.com/tango-controls/cppTango/issues/702))
- Safe interworking between read_attribute() and push_event() ([cppTango#698](https://github.com/tango-controls/cppTango/issues/698))

## AOB

### HDB++

The next HDB++ meeting teleconference meeting will take place on Thursday 18th June at 14:00 CEST.

#### TangoDatabase DS

Anton detected that the version number in the CMakeLists.txt and Makefile are not in sync with the latest version.
Thomas created a PR to fix this issue ([TangoDatabase#22](https://github.com/tango-controls/TangoDatabase/pull/22)).

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

The next Tango kernel teleconf meeting will take place in 2 weeks on Thursday 11th June 2020 at 15:00 CEST.

## Summary of remaining actions

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

**Action - Soleil**: Fix last issues with events in JTango and release a new JTango version which will be used in the next Tango Source Distribution release.

**Action - SKA-ZA**: Create an issue in [TangoTickets repository](https://github.com/tango-controls/TangoTickets) to give more details about the idea of using APM and OpenTracing.

**Action - Byte Physics**: Clarify with Gwenaelle about Java 8 and 11 support in latest JTango version.
Is there anything to be done to get a Java 8 or 11 compatible version from latest 9.6.0 draft release?

**Action - STFC/ALBA**: Geoff will send a question on Tango mailing list and/or Tango Kernel mailing list related to the 
DevEncoded usage in PyTango and the expected python types. Sergi will pass the question to his team in ALBA.

**Action - ESRF**: Send link to Geoff to give him access to a recent pytango conda package (beta version)
