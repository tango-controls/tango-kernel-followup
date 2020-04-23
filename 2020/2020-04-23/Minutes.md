# Tango Kernel Follow-up Meeting - 2020/04/23

Held on 2020/04/23 at 15:00 CEST on Zoom.

Participants:  
               
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

**Action - S2Innovation**: Create a placeholder section in the documentation listing the known work-arounds for known issues and 
things to avoid when programming with Tango.

**Action - ESRF**: Get some information about the process to build a new Tango Source Distribution Windows Binary release and who did it the last time.
**Got some information from Emmanuel Taurel about the manuel process which was used to build 9.2.2 Windows distribution.
This should be automated and is a big work.**

**Action - Byte Physics**: TangoSourceDistribution: Warn the user if Java version > 8 is detected that Pogo is currently supported on Java 8 only.

**Action - Elettra**: Propose a Pull Request to remove warning related to an unneeded comma in 9.3-backports branch

**Action - Byte Physics**: Investigate on automatic appveyor artifacts upload as github release assets  ([cppTango#602](https://github.com/tango-controls/cppTango/pull/602)).

**Action - ESRF**: Clarify with Gwenaelle Abeillé and Pascal Verdier what has been fixed in JTango ([commit 2acbab4](https://github.com/tango-controls/JTango/commit/2acbab4874b6e47f0a6b482f7aa2f104207dfc79)) and whether the fix is consistent with cppTango behaviour.
**Inconsistency has been confirmed by Pascal Verdier who sent an e-mail to Gwenaelle.**

**Action - ESRF**: Prepare a TangoTest conda package. **New release of TangoTest with CMake will be released soon.**

**Action - ESRF**: Upload new conda packages to official tango-controls conda channel. **No progress**

**Action - SKA-ZA**: Create an issue in [TangoTickets repository](https://github.com/tango-controls/TangoTickets) to give more details about the idea of using APM and OpenTracing.

## cppTango News

### Recent PR merged
Several PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:

#### 9.3 backports
- Fix issue where unsubscribing in push_events led to API_EventTimeout 
([cppTango#686](https://github.com/tango-controls/cppTango/issues/686), 
[cppTango#699](https://github.com/tango-controls/cppTango/pull/699))

### New issues
- 9.3-backports: Feedback on compiling on MacOSX Sierra ([cppTango#705](https://github.com/tango-controls/cppTango/issues/705))
- build failure cppTango arch: openbsd ([cppTango#706](https://github.com/tango-controls/cppTango/issues/706))

### Recent developments
- Correct archive periodic event sending after polling restart ([cppTango#704](https://github.com/tango-controls/cppTango/pull/704))

### PR merge goals for next meeting
Here is the list of opened PR with "Ready for Merge" label: https://github.com/tango-controls/cppTango/pulls?q=is%3Apr+is%3Aopen+label%3A%22Ready+For+Merge%22

## JTango News

## PyTango News

## Tango Source Distribution

### New issues
- Ensure we have a working sed ([#73](https://github.com/tango-controls/TangoSourceDistribution/issues/73))

### Recent development
- Upgrade rest server to 1.18 ([#74](https://github.com/tango-controls/TangoSourceDistribution/pull/74))
- .travis.yml: Fix broken build due to changes in tango-doc repository 
([#72](https://github.com/tango-controls/TangoSourceDistribution/issues/72),
 [#75](https://github.com/tango-controls/TangoSourceDistribution/pull/75))

## Conda packages

### Tango meeting 2020

## High priorities issues

- appveyor: Add support for automatic uploading of releases to github ([cppTango#602](https://github.com/tango-controls/cppTango/issues/602))

## AOB

### HDB++

An HDB++ meeting teleconference took place on Wednesday 15th April.
The minutes of the meetings are available on github: 
https://github.com/tango-controls-hdbpp/meeting-minutes/blob/master/2020-04-15/Minutes.md

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
