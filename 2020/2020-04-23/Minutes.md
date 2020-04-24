# Tango Kernel Follow-up Meeting - 2020/04/23

Held on 2020/04/23 at 15:00 CEST on Zoom.

Participants:  Reynald Bourtembourg, Andrew Goetz (ESRF), Sergi Rubio (ALBA), Gwenaelle Abeillé (SOLEIL),
Loenzo Pivetta (ELETTRA), Geoffrey Mant(STFC), Michal Liszcz (S2Innovation), Thomas Braun (Byte Physics)
               
# Minutes

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2020/2020-09/Minutes.md#summary-of-remaining-actions)

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
**Done: https://tango-controls.readthedocs.io/en/latest/administration/deployment/versions-in-use.html?highlight=DESY#tango-controls-versions-in-use**

**Action - S2Innovation**: Create a placeholder section in the documentation listing the known work-arounds for known issues and 
things to avoid when programming with Tango.  
**Done: https://tango-controls.readthedocs.io/en/latest/development/advanced/known-issues.html.
Alba is currently preparing 4-5 known issues and work-around and will contribute to add content to this documentation section.**

**Action - ESRF**: Get some information about the process to build a new Tango Source Distribution Windows Binary release and who did it the last time.  
**Got some information from Emmanuel Taurel about the manuel process which was used to build 9.2.2 Windows distribution.
This should be automated and is a big work. Thomas is interested in working in this topic but would like to finish the other 
tasks he started to work on first.**

**Action - Byte Physics**: TangoSourceDistribution: Warn the user if Java version > 8 is detected that Pogo is currently supported on Java 8 only.

**Action - Elettra**: Propose a Pull Request to remove warning related to an unneeded comma in 9.3-backports branch.  
**Lorenzo created [cppTango#708](https://github.com/tango-controls/cppTango/pull/708) for tango-9-lts and Thomas created the equivalent 9.3-backports PR 
([cppTango#709](https://github.com/tango-controls/cppTango/pull/709))**

**Action - Byte Physics**: Investigate on automatic appveyor artifacts upload as github release assets  ([cppTango#602](https://github.com/tango-controls/cppTango/pull/602)).  
**Thomas uploaded manually (semi-automatic) artifacts for 9.3.4-rc4 version and shared his recipe.
He also added a personal access token which hopefully will fix the issue.**

**Action - ESRF**: Clarify with Gwenaelle Abeillé and Pascal Verdier what has been fixed in JTango ([commit 2acbab4](https://github.com/tango-controls/JTango/commit/2acbab4874b6e47f0a6b482f7aa2f104207dfc79)) and whether the fix is consistent with cppTango behaviour.  
**Inconsistency has been confirmed by Pascal Verdier who sent an e-mail to Gwenaelle.
Gwenaelle confirmed she got the e-mail and has understood what needs to be done. She will work on this soon.**

**Action - ESRF**: Prepare a TangoTest conda package.  
**New release of TangoTest with CMake will be released soon.**

**Action - ESRF**: Upload new conda packages to official tango-controls conda channel.  
**No progress**

**Action - SKA-ZA**: Create an issue in [TangoTickets repository](https://github.com/tango-controls/TangoTickets) to give more details about the idea of using APM and OpenTracing.

## cppTango News

### Recent PR merged
Several PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:

#### tango-9-lts (future 9.4)
- Always allow to change attribute alarm thresholds 
([cppTango#401](https://github.com/tango-controls/cppTango/issues/401),
[cppTango#692](https://github.com/tango-controls/cppTango/pull/692))
- Send attribute configuration event to all clients after device restart 
([cppTango#361](https://github.com/tango-controls/cppTango/issues/361), 
[cppTango#694](https://github.com/tango-controls/cppTango/pull/694))) 

#### 9.3 backports
- Fix issue where unsubscribing in push_events led to API_EventTimeout 
([cppTango#686](https://github.com/tango-controls/cppTango/issues/686), 
[cppTango#699](https://github.com/tango-controls/cppTango/pull/699))

### New issues
- 9.3-backports: Feedback on compiling on MacOSX Sierra ([cppTango#705](https://github.com/tango-controls/cppTango/issues/705))
- build failure cppTango arch: openbsd ([cppTango#706](https://github.com/tango-controls/cppTango/issues/706))

Giacomo found a solution to compile cppTango on OpenBSD and said on Github he would provide some patches.
This will hopefully solve as well the issues seen on Mac OS X Sierra.
These new issues raised a question from Anton about whether we should support Tango on Mac or many different OS?  
Thomas suggested that we could decide to support only the Tango client part for instance on these OS.  
Reynald said that if we can make Tango work on these systems without too much effort, we should do it, on a best effort basis.  
Users won't have a standard support on these OS but the more users there will be, the bigger the community to help these users will be too.

### Recent developments
- Correct archive periodic event sending after polling restart ([cppTango#704](https://github.com/tango-controls/cppTango/pull/704))

### PR merge goals for next meeting
Here is the list of opened PR with "Ready for Merge" label: https://github.com/tango-controls/cppTango/pulls?q=is%3Apr+is%3Aopen+label%3A%22Ready+For+Merge%22

We agreed to set as recurrent goal to review carefully and merge (if approved, of course) the PRs having the "Ready for Merge label" set, 
prioritizing the PR having the "High Priority" label and the external contributions.

Here is the list of PR which were with the "Ready For Merge" label at the time of this teleconf meeting:
- [702](https://github.com/tango-controls/cppTango/pull/702) (high priority)
- [698](https://github.com/tango-controls/cppTango/pull/698) (high priority)
- [688](https://github.com/tango-controls/cppTango/pull/688) (external contribution)
- [703](https://github.com/tango-controls/cppTango/pull/703) 
- [700](https://github.com/tango-controls/cppTango/pull/700)
- [697](https://github.com/tango-controls/cppTango/pull/697)
- [673](https://github.com/tango-controls/cppTango/pull/673)
- [659](https://github.com/tango-controls/cppTango/pull/659)
- [574](https://github.com/tango-controls/cppTango/pull/574)
- [564](https://github.com/tango-controls/cppTango/pull/564)

### Conan packages

Thomas proposed to invite Marius Elvert to our Tango kernel teleconf meetings. He will be invited to the next meeting.
Soleil is starting to use Conan.

**Action - ESRF**: Invite Marius Elvert to the next Tango Kernel Teleconf meeting

## JTango News

Gwenaelle has fixed some bugs related to the events but there is still some work to be done to be consistent with 
cppTango behaviour.  
A new release will be needed for the Tango Source Distribution

**Action - Soleil**: Fix last issues with events in JTango and release a new JTango version which will be used in the next Tango Source Distribution release.

## PyTango News

Alba asked Anton to go on with the new PyTango release. The issue which was a blocking point before will be solved later.

Anton will investigate on the memory leak issue and will try to remove the suspicious line, as suggested by Reynald in a github comment.

No progress on PyBind11 porting. Geoff is currently busy working for SKA. He will probably be able to work on PyBind11 
again for a couple of weeks at the end of May.

Tiago and Jairo have been working on 2 PyTango issues (WIP).

## Tango Source Distribution

### New issue
- Ensure we have a working sed ([#73](https://github.com/tango-controls/TangoSourceDistribution/issues/73))

Thomas said sed (funny!) is no longer used in cppTango tango-9-lts. This fix could be backported to the concerned Makefile.am file.

### Recent development
- .travis.yml: Fix broken build due to changes in tango-doc repository  ([#75](https://github.com/tango-controls/TangoSourceDistribution/pull/75),
[#72](https://github.com/tango-controls/TangoSourceDistribution/issues/72))

## Conda packages

Reynald will soon release a new TangoTest version which can be built using CMake.
This version will be used to build the TangoTest Conda Package.

Reynald asked how to handle the debug version of the cppTango library.
Should we create a cppTango debug package? Should we provide the debug version in the same package as the release version and 
install it in another directory (CMAKE_INSTALL_PREFIX/lib/debug)?
If we create 1 package for the release version and 1 package for the debug version, 
do we allow to install them both on the same conda environment (2 different install locations?)?

### Tango meeting 2020

The Tango meeting will not take place in June in Russia.  
Discussions with IK and the Steering Committee will take place in the coming week.

## High priorities issues

- appveyor: Add support for automatic uploading of releases to github ([cppTango#602](https://github.com/tango-controls/cppTango/issues/602))
- Backport fix for #496 and #361 - event clients lost after dev restart ([cppTango#702](https://github.com/tango-controls/cppTango/issues/702))
- Safe interworking between read_attribute() and push_event() ([cppTango#698](https://github.com/tango-controls/cppTango/issues/698))

## AOB

### HDB++

An HDB++ meeting teleconference took place on Wednesday 15th April.
The minutes of the meeting are available on github: 
https://github.com/tango-controls-hdbpp/meeting-minutes/blob/master/2020-04-15/Minutes.md

### Docker

Sergi asked the following question:
Which is currently the best source for deploying a docker-based Tango
Control System?:
 - https://github.com/tango-controls/tango-cs-docker , updated 15 months ago (more stable)
or
 - https://github.com/ska-telescope/ska-docker , updated 2 days ago (more recent)

Michal mentioned that these docker images do not provide exactly the same parts of Tango software.
tango-cs docker is updated when a new Tango Source Distribution official release is available.

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

The next Tango kernel teleconf meeting will take place **in 3 weeks** on Thursday 14th May 2020 at 15:00 CEST.

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

**Action - Alba**: Add content to known issues section of the documentation to share some known work-around tricks.

**Action - Byte Physics**: TangoSourceDistribution: Warn the user if Java version > 8 is detected that Pogo is currently supported on Java 8 only.

**Action - ESRF**: Invite Marius Elvert to the next Tango Kernel Teleconf meeting

**Action - Soleil**: Fix last issues with events in JTango and release a new JTango version which will be used in the next Tango Source Distribution release.

**Action - ESRF**: Prepare a TangoTest conda package.

**Action - ESRF**: Upload new conda packages to official tango-controls conda channel.

**Action - SKA-ZA**: Create an issue in [TangoTickets repository](https://github.com/tango-controls/TangoTickets) to give more details about the idea of using APM and OpenTracing.
