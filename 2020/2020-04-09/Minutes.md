# Tango Kernel Follow-up Meeting - 2020/04/09

Held on 2020/04/09 at 15:00 CEST on Zoom.

Participants:  Lorenzo Pivetta (Elettra), Anton Joubert (SKA-ZA), Thomas Braun (Byte Physics),
               Michal Liszcz (S2Innovation), Andrew Goetz and Reynald Bourtembourg (ESRF)
               
# Minutes

## Tango Source Distribution

cppTango 9.3.4-rc4 has been released.

Tango Source Distribution 9.3.4-rc4 is waiting for a new JTango release containing the bug fixes for the events and Java 11 support.

Thomas created [JTango#101](https://github.com/tango-controls/JTango/issues/101) just after the meeting to ask for a new JTango release.

Andy said it would be good to create a new Windows binary release.

**Action - ESRF**: Get some information about the process to build a new Tango Source Distribution Windows Binary release and who did it the last time.

**Action - Byte Physics**: TangoSourceDistribution: Warn the user if Java version > 8 is detected that Pogo is currently supported on Java 8 only.

## cppTango News

cppTango 9.3.4-rc4 release has been created.
 
It has been deployed on PPC platform at Elettra. No issue so far except a small compilation issue with old compilers.

Reynald said that this is a known issue and a work-around was specified in cppTango release notes. Here it is:

```
We added -pedantic flag when compiling with g++ or Clang in debug mode.
This change can generate build errors with very old compilers (e.g. g++ 3.4.6) when compiling the library debug version. 
Please remove manually -pedantic flag in configure/CMakeLists.txt if you need to compile the debug version on a very old compiler.
```

Since this warning seemed to be due only to an unnecessary comma, we agreed we could fix it on 9.3-backports branch by simply removing this comma in this branch.

**Action - Elettra**: Propose a Pull Request to remove warning related to an unneeded comma in 9.3-backports branch
 
Automatic appveyor artifacts upload as github release assets failed. To be investigated.
Thomas volunteered to have a look at it.

**Action - Byte Physics**: Investigate on automatic appveyor artifacts upload as github release assets  ([cppTango#602](https://github.com/tango-controls/cppTango/pull/602)).

### Recent PR merged
Several PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:
#### In tango-9-lts
- Allow different paths for CPPZMQ and ZMQ ([cppTango#642](https://github.com/tango-controls/cppTango/pull/642))
- Enforce non-interactive package installation in CI ([cppTango#701](https://github.com/tango-controls/cppTango/pull/701))

#### 9.3 backports
- Update ChangeLog for 9.3.4 ([cppTango#672](https://github.com/tango-controls/cppTango/pull/672))

### New issues
- No new issue reported since the previous kernel teleconf meeting (2020-03-26)

### Recent developments

- Shared/static switching on Windows ([cppTango#688](https://github.com/tango-controls/cppTango/pull/688)) - Ready!
Waiting for review. Probably need some cleanup in the commits, unless a squash merge is chosen.
- Backport fix for [cppTango#496](https://github.com/tango-controls/cppTango/issues/496) and [cppTango#361](https://github.com/tango-controls/cppTango/issues/361)
([cppTango#702](https://github.com/tango-controls/cppTango/pull/702)). Ready for review?
- Fix [cppTango#693](https://github.com/tango-controls/cppTango/issues/693): pipe events are lost after RestartServer command ([cppTango#703](https://github.com/tango-controls/cppTango/pull/703)). Ready for review
- Upgrade llvm in warning as errors CI tests ([cppTango#700](https://github.com/tango-controls/cppTango/pull/700)). 
Small indentation issue. 
Maybe we should raise the priority for [cppTango#586](https://github.com/tango-controls/cppTango/issues/586) which should 
bring automatic code formatting? We will proceed by steps. The work will be done first in tango-9-lts branch (and maybe only on this branch).
First the results of the automatic code formatting will have to be available to the kernel developers. We can then fine tune it.
When we will be happy with the results, we will first concentrate on merging pending pull requests to reduce the impact of merging 
this big pull request which will have an impact on all files. Thomas volunteered to work on this issue he created himself.
- Fix issue where unsubscribing in push_events led to API_EventTimeout ([cppTango#686](https://github.com/tango-controls/cppTango/issues/686),
[cppTango#699](https://github.com/tango-controls/cppTango/pull/699)). Ready to be tested by Alba. Already approved by Michal. 
Need 1 more approval. Thomas will have a look.

Michal suggested to concentrate on reviewing pull requests which are ready for merge and proposed to give a list of the ones requiring reviews 
in these minutes. He also proposed to define some goals to merge/review a list of PRs from one Kernel Meeting to another.
In any case, the kernel developers need to have a look at the PRs where their review has been requested.
We should focus in priority on the PRs with no conflicts and having the "Ready for Merge" label.

Here is the list of opened PR with "Ready for Merge" label: https://github.com/tango-controls/cppTango/pulls?q=is%3Apr+is%3Aopen+label%3A%22Ready+For+Merge%22

**Action - Kernel developers**: Look at https://github.com/pulls/review-requested and review/merge pending PRs

### Other issues with no activities since last teleconf and requiring review or feedback
- All the issues waiting for a feedback from issue reporter or community: https://github.com/tango-controls/cppTango/labels/question
- Remove fallback snprintf implementation ([cppTango#659](https://github.com/tango-controls/cppTango/pull/659)).
Review from Michal done, waiting for an answer.
- Switch to python3 for tests ([cppTango#673](https://github.com/tango-controls/cppTango/pull/673)). Waiting for review.
- Ensure location transparency for image and spectrum attributes ([cppTango#697](https://github.com/tango-controls/cppTango/pull/697))
Waiting for review
- Send attribute configuration event to all clients after device restart ([cppTango#694](https://github.com/tango-controls/cppTango/pull/694))
Waiting for review
- Safe interworking between read_attribute() and push_event() ([cppTango#698](https://github.com/tango-controls/cppTango/pull/698)). 
Waiting for review. This is a large PR which requires careful review.
- Fix 566 const reference parameters ([cppTango#574](https://github.com/tango-controls/cppTango/pull/574)). Waiting for review

A review of the old PRs and opened issues will be needed at some point to do some clean up and to ping the issue reporters and identify what is the 
blocking point of each stalled issue/PR.

## JTango News

fix bug in checkEventCriteria (used at event subscription) and avoid pushing events from polling if pushing from code is activated.
Was this really a bug? Reynald thinks cppTango behaves the same. Is it a bug or a feature?

**Action - ESRF**: Clarify with Gwenaelle Abeillé and Pascal Verdier what has been fixed in JTango ([commit 2acbab4](https://github.com/tango-controls/JTango/commit/2acbab4874b6e47f0a6b482f7aa2f104207dfc79)) and whether the fix is consistent with cppTango behaviour.

## PyTango News

- PyTango new release is waiting for a fix from Alba.

- Memory leak when pushing DevEncoded change events at high rate [TangoTickets#30](https://github.com/tango-controls/TangoTickets/issues/30).
This issue could not be reproduced in cppTango. Reynald detected something suspicious in pyTango related code.

- Anton asked where he should copy the documentation they have written in SKA related to pyTango testing features.
This documentation is currently on SKA confluence and not available to the general public.
If it is copied on pyTango readthedocs, no result will appear when searching for these features from tango readthedocs search box.
The compromise is to put it in pytango readthedocs and to put a small description on tango readthedocs too.

## Conda packages

Anton asked for a TangoTest conda package.

**Action - ESRF**: Prepare a TangoTest conda package

A Pull request was recently merged in itango repository, providing a conda recipe for itango.
It might be useful to provide an itango conda recipe in [pytango-conda-recipes repository](https://github.com/tango-controls/pytango-conda-recipes) 
for official itango releases.

It might make sense to merge pytango-conda-recipes and tango-conda-recipes repositories.

**Action - ESRF**: Upload new conda packages to official tango-controls conda channel

### Tango meeting 2020

Due to COVID-19, there is a very low probability that the Tango meeting will take place as originally foreseen in June.
A decision to eventually postpone it to Autumn will have to be taken around end of April.

## High priorities issues

- [cppTango#686](https://github.com/tango-controls/cppTango/issues/686) should be fixed in [cppTango#699](https://github.com/tango-controls/cppTango/pull/699).

## AOB

### HDB++

The next HDB++ meeting teleconference will take place on Wednesday 15th April at 10:00 CEST.

The main goals of this meeting will be to get a status update of the HDB++ project.

Since Stuart James will leave the ESRF at the end of week 16 (~17th April), this meeting  will mainly focus on a status 
update of what Stuart has been doing, on the eventual impact on the different HDB++ components and on what remains to be done.
We will also introduce Damien Lacoste who has been hired recently by the ESRF and who already started to work on the HDB++ project with Stuart.
This will also be the opportunity to get some feedback from the persons who have been using/testing the HDB++ software 
and of course to share opinions on the future developments of the HDB++ software.

Lorenzo proposed to think about organizing a face-to-face HDB++ meeting nearby the end of 2020.
We will discuss this in May when we'll have more information about the Tango meeting.

### omniORB 4.3.0

omniORB 4.3.0 beta 1 has been released. Here are the release notes:

```
omniORB 4.3 has a number of new features and changes:

 - A new omniORB-specific HTTP / HTTPS transport, with a number of
   capabilities:

    . Full encapsulation of GIOP messages in HTTP.

    . Support for web proxies, transparent web proxies, reverse proxies.

    . For cases where security is important but an end-to-end HTTPS
      connection cannot be assured, support for in-message encryption.

 - Support for vast CORBA messages on 64 bit platforms.

 - Support for PyPy in omniidl and omniORBpy.

 - omniCallDescriptor::current() and omniCallHandle::current() to
   access information about the current call on a server.

 - The sslContext class is now in the omni namespace.
```

omniORB 4.2.4 has been released too and now supports C++17 compilers.

### OpenTracing

SKA suggested to use [OpenTracing](https://opentracing.io) technologies to help tracing commands and profiling Tango applications and [APM](https://www.elastic.co/apm).

**Action - SKA-ZA**: Create an issue in [TangoTickets repository](https://github.com/tango-controls/TangoTickets) to give more details about the idea of using APM and OpenTracing.

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

The next Tango kernel teleconf meeting will take place in 2 weeks on Thursday 23rd April 2020 at 15:00 CEST.

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2020/2020-03-26/Minutes.md#summary-of-remaining-actions)

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

**Action - S2Innovation**: Create a page in tango-doc where each institute could list the operating systems where cppTango and PyTango are running in their institutes.
It could probably be interesting to list as well the java versions used for the JTango applications.
**Some replies have been received by the different institutes. The results will be presented soon**.

**Action - S2Innovation**: Attempt to backport [cppTango#573](https://github.com/tango-controls/cppTango/pull/573) and 
[cppTango#694](https://github.com/tango-controls/cppTango/pull/694). 
**Done in ([cppTango#702](https://github.com/tango-controls/cppTango/pull/702)), waiting for review.**

**Action - S2Innovation?**: Create a section in the documentation listing the known work-arounds for known issues and 
things to avoid when programming with Tango.
**We agreed that S2Innovation will only create a placeholder for the moment for this section.
Contributors will have to create Pull Requests to add content**

**Action - Tango conda users**: Test new cppTango conda package available as artifact here: https://github.com/bourtemb/tango-conda-recipes/runs/519928988
**Tested by Anton**

**Action - ESRF**: Reynald will send a framadate poll to find a good date for an HDB++ teleconf meeting.
**Done: meeting will take place on Wednesday 15th April at 10:00 CEST**

**Action - ESRF**: Create a new issue for batching events subscriptions improvement. 
**Done: See [TangoTickets#33](https://github.com/tango-controls/TangoTickets/issues/33)**

## Summary of remaining actions

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - Kernel developers**: Look at https://github.com/pulls/review-requested and review/merge pending PRs

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - All**: Test [9.3.4-rc4](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc4) release when it will be out.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the 
TangoSourceDistribution repository.

**Action - S2Innovation**: Create a page in tango-doc where each institute could list the operating systems where cppTango and PyTango are running in their institutes.
It could probably be interesting to list as well the java versions used for the JTango applications.

**Action - S2Innovation**: Create a placeholder section in the documentation listing the known work-arounds for known issues and 
things to avoid when programming with Tango.

**Action - ESRF**: Get some information about the process to build a new Tango Source Distribution Windows Binary release and who did it the last time.

**Action - Byte Physics**: TangoSourceDistribution: Warn the user if Java version > 8 is detected that Pogo is currently supported on Java 8 only.

**Action - Elettra**: Propose a Pull Request to remove warning related to an unneeded comma in 9.3-backports branch

**Action - Byte Physics**: Investigate on automatic appveyor artifacts upload as github release assets  ([cppTango#602](https://github.com/tango-controls/cppTango/pull/602)).

**Action - ESRF**: Clarify with Gwenaelle Abeillé and Pascal Verdier what has been fixed in JTango ([commit 2acbab4](https://github.com/tango-controls/JTango/commit/2acbab4874b6e47f0a6b482f7aa2f104207dfc79)) and whether the fix is consistent with cppTango behaviour.

**Action - ESRF**: Prepare a TangoTest conda package

**Action - ESRF**: Upload new conda packages to official tango-controls conda channel

**Action - SKA-ZA**: Create an issue in [TangoTickets repository](https://github.com/tango-controls/TangoTickets) to give more details about the idea of using APM and OpenTracing.
