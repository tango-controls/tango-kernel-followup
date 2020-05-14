# Tango Kernel Follow-up Meeting - 2020/05/14

Held on 2020/05/14 at 15:00 CEST on Zoom.

Participants:  Reynald Bourtembourg, Andrew Goetz (ESRF), Sergi Rubio (ALBA), Gwenaelle Abeillé (SOLEIL),
Lorenzo Pivetta (ELETTRA), Geoffrey Mant(STFC), Michal Liszcz (S2Innovation), Thomas Braun (Byte Physics),
Marius Elvert (Software Schneiderei)
               
# Minutes

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2020/2020-23/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - Kernel developers**: Look at https://github.com/pulls/review-requested and review/merge pending PRs

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - All**: Test [9.3.4-rc4](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc4) release when it will be out.  
**[9.3.4-rc4](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc4) is out!**

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the 
TangoSourceDistribution repository.

**Action - Alba**: Add content to known issues section of the documentation to share some known work-around tricks.

**Action - Byte Physics**: TangoSourceDistribution: Warn the user if Java version > 8 is detected that Pogo is currently supported on Java 8 only.

**Action - ESRF**: Invite Marius Elvert to the next Tango Kernel Teleconf meeting. **Done**

**Action - Soleil**: Fix last issues with events in JTango and release a new JTango version which will be used in the next Tango Source Distribution release.

**Action - ESRF**: Prepare a TangoTest conda package. 
**PR [tango-conda-recipes#2](https://github.com/tango-controls/tango-conda-recipes/pull/5) created and to be reviewed.**

**Action - ESRF**: Upload new conda packages to official tango-controls conda channel. **tango-idl and cpptango conda packages uploaded to tango-controls conda channel**

**Action - SKA-ZA**: Create an issue in [TangoTickets repository](https://github.com/tango-controls/TangoTickets) to give more details about the idea of using APM and OpenTracing.

## cppTango News

cppTango 9.3.4-rc5 has been released.

Since last week, ESRF is using cppTango 9.4.0-rc0 (esrf-9.4.0-rc0 tag from cppTango bourtemb's fork) version for the device servers controlling the White Rabbit timing devices.

### Recent PR merged
Several PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:

#### tango-9-lts (future 9.4)
- Fix tango const comma ([cppTango#708](https://github.com/tango-controls/cppTango/pull/708))
- Remove fallback snprintf implementation ([cppTango#659](https://github.com/tango-controls/cppTango/pull/659))
- Upgrade llvm in warning as errors CI tests ([cppTango#700](https://github.com/tango-controls/cppTango/pull/700))
- Switch to python3 for tests ([cppTango#673](https://github.com/tango-controls/cppTango/pull/673), [cppTango#695](https://github.com/tango-controls/cppTango/issues/695))
- .travis/gcc-latest/Dockerfile: Update to 10.1.0 ([cppTango#717](https://github.com/tango-controls/cppTango/pull/717))

#### 9.3 backports
- Remove extra comma ([cppTango#709](https://github.com/tango-controls/cppTango/pull/709))
- Update CHANGELOG for #699 ([cppTango#707](https://github.com/tango-controls/cppTango/pull/707))


### New issues
- Travis CI potential optimization: No need to clone and install tango_admin when RUN_TESTS=OFF ([cppTango#710](https://github.com/tango-controls/cppTango/issues/710))
- Remove log4tango/threading utilities ([cppTango#712](https://github.com/tango-controls/cppTango/issues/712))
- Remove custom ostringstream implementation ([cppTango#713](https://github.com/tango-controls/cppTango/issues/713))
- Replace deprecated std functions ([cppTango#714](https://github.com/tango-controls/cppTango/issues/714))
- tango.pc(.cmake) file improvements? ([cppTango#718](https://github.com/tango-controls/cppTango/issues/718))

### Recent developments
- Build failure cppTango arch: openbsd ([cppTango#706](https://github.com/tango-controls/cppTango/pull/706)). Waiting for Giacomo's green light?
- configure/CMakeLists.txt: Use dpkg-buildflags flags for debug builds ([cppTango#715](https://github.com/tango-controls/cppTango/pull/715))
- Fix nb_endpoints in ZmqEventConsumer::connect_event_channel ([cppTango#716](https://github.com/tango-controls/cppTango/pull/716))
-  Automate abi api compliance check ([cppTango#662](https://github.com/tango-controls/cppTango/pull/662))
- Ensure location transparency for image and spectrum attributes ([cppTango#697](https://github.com/tango-controls/cppTango/pull/697))

## PR Merge goals from last meeting
Here is the list of PR which were with the "Ready For Merge" label at the time of the previous teleconf meeting:
- [cppTango#702](https://github.com/tango-controls/cppTango/pull/702) (high priority)  **1 approval missing**
- [cppTango#698](https://github.com/tango-controls/cppTango/pull/698) (high priority)  **Still waiting for review**
- [cppTango#688](https://github.com/tango-controls/cppTango/pull/688) (external contribution) **Changes requested**
- [cppTango#703](https://github.com/tango-controls/cppTango/pull/703) **Still waiting for review**
- [cppTango#700](https://github.com/tango-controls/cppTango/pull/700) **Merged**
- [cppTango#697](https://github.com/tango-controls/cppTango/pull/697) **Issue with the tests?**
- [cppTango#673](https://github.com/tango-controls/cppTango/pull/673) **Merged**
- [cppTango#659](https://github.com/tango-controls/cppTango/pull/659) **Merged**
- [cppTango#574](https://github.com/tango-controls/cppTango/pull/574) **1 approval missing**
- [cppTango#564](https://github.com/tango-controls/cppTango/pull/564) **1 approval missing**

### PR merge goals for next meeting
Here is the list of opened PR with "Ready for Merge" label: https://github.com/tango-controls/cppTango/pulls?q=is%3Apr+is%3Aopen+label%3A%22Ready+For+Merge%22

We agreed to set as recurrent goal to review carefully and merge (if approved, of course) the PRs having the "Ready for Merge label" set, 
prioritizing the PR having the "High Priority" label and the external contributions.

Here is the list of PR which were with the "Ready For Merge" label at the time of this teleconf meeting:
- [cppTango#702](https://github.com/tango-controls/cppTango/pull/702) (high priority)
- [cppTango#698](https://github.com/tango-controls/cppTango/pull/698) (high priority)
- [cppTango#688](https://github.com/tango-controls/cppTango/pull/688) (external contribution)
- [cppTango#685](https://github.com/tango-controls/cppTango/pull/685) (external contribution)
- [cppTango#703](https://github.com/tango-controls/cppTango/pull/703) 
- [cppTango#574](https://github.com/tango-controls/cppTango/pull/574)
- [cppTango#564](https://github.com/tango-controls/cppTango/pull/564)
- [cppTango#715](https://github.com/tango-controls/cppTango/pull/715)
- [cppTango#702](https://github.com/tango-controls/cppTango/pull/702)

## JTango News

## PyTango News

## Tango Source Distribution

TangoSourceDistribution 9.3.4-4 has been released.

## Conan packages

## Conda packages

### tango-test conda package
TangoTest 3.0 has been released (first release using CMake).  
PR [tango-conda-recipes#2](https://github.com/tango-controls/tango-conda-recipes/pull/5) for tango-test conda package has been created and is to be reviewed.

### pytango conda package
Reynald started to work on building a new pytango conda package and got the following errors during the conda build process: 

```
ld: cannot find -lboost_python
```

### Storage limitations on anaconda cloud

Tiago warned Reynald via e-mail that anaconda cloud has a limit of 3 GB for tango-controls conda channel packages.  
Current usage is ~458 MB (14% Full).  
This 3GB limit might be an issue in the future if many packages or versions of these packages are created.

### Tango meeting 2020

The Tango meeting will not take place in June in Russia. It is postponed to 17th to 19th November 2020, still in Saint Petersburg.

The TANGO steering committee has decided to do a TANGO status update in the form of a webinar on 10th June 2020.

## High priorities issues

- appveyor: Add support for automatic uploading of releases to github ([cppTango#602](https://github.com/tango-controls/cppTango/issues/602))
- Backport fix for #496 and #361 - event clients lost after dev restart ([cppTango#702](https://github.com/tango-controls/cppTango/issues/702))
- Safe interworking between read_attribute() and push_event() ([cppTango#698](https://github.com/tango-controls/cppTango/issues/698))

## AOB

### HDB++

The next HDB++ meeting teleconference meeting will take place on ? (Wednesday, June 17, 2020 - 10:00?).

https://framadate.org/bFCxIwXUYgbOAchY

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

The next Tango kernel teleconf meeting will take place **in 2 weeks** on Thursday 28th May 2020 at 15:00 CEST.

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

**Action - Byte Physics**: TangoSourceDistribution: Warn the user if Java version > 8 is detected that Pogo is currently supported on Java 8 only.

**Action - Soleil**: Fix last issues with events in JTango and release a new JTango version which will be used in the next Tango Source Distribution release.

**Action - ESRF**: Prepare a TangoTest conda package.

**Action - SKA-ZA**: Create an issue in [TangoTickets repository](https://github.com/tango-controls/TangoTickets) to give more details about the idea of using APM and OpenTracing.
