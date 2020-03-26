# Tango Kernel Follow-up Meeting - 2020/03/26

Held on 2020/03/26 at 15:00 CET on https://esrf.zoom.us/j/936186697

Participants:  

# Minutes

## Tango Source Distribution

## cppTango News

### Recent PR merged
Several PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:
#### In tango-9-lts
- Fix #496 blind event clients after dev restart ([cppTango#573](https://github.com/tango-controls/cppTango/pull/573))
- Cleanup Taco ([cppTango#655](https://github.com/tango-controls/cppTango/pull/655))

#### 9.3 backports
- 9.3 backport to fix #330 ([cppTango#681](https://github.com/tango-controls/cppTango/pull/681)) (Segmentation fault after execution state command/attribute, at check_level_alarm)

### New issues
The following issues and pull requests have been created since the last teleconf meeting and are not yet solved:
- Pipe event subscriptions are lost after RestartServer command ([cppTango#693](https://github.com/tango-controls/cppTango/issues/693))
- Fix python warnings/errors in cxxtestgen.py ([cppTango#695](https://github.com/tango-controls/cppTango/issues/695))

### Recent developments

- Always allow to change attribute alarm thresholds ([cppTango#692](https://github.com/tango-controls/cppTango/pull/692)). 
Waiting for review.
- Shared/static switching on Windows ([cppTango#688](https://github.com/tango-controls/cppTango/pull/688))
Marius is proposing  proposing to provide a package with dynamic libraries, containing the debug and release versions in 
the same package, and to provide a separate package for static libraries, containing also release and debug versions in 
the same package. Please comment on the ticket if you have some objections or better ideas.
- Remove fallback snprintf implementation ([cppTango#659](https://github.com/tango-controls/cppTango/pull/659)).
Review from Michal done, waiting for an answer.
- Switch to python3 for tests ([cppTango#673](https://github.com/tango-controls/cppTango/pull/673)). Waiting for review.
- Ensure location transparency for image and spectrum attributes ([cppTango#697](https://github.com/tango-controls/cppTango/pull/697))
Waiting for review
- Allow different paths for CPPZMQ and ZMQ ([cppTango#642](https://github.com/tango-controls/cppTango/pull/642)). 
Reviewed and ready for merge. Candidate for 9.3 backport?
- Send attribute configuration event to all clients after device restart ([cppTango#694](https://github.com/tango-controls/cppTango/pull/694))
Waiting for review
- Safe interworking between read_attribute() and push_event() ([cppTango#698](https://github.com/tango-controls/cppTango/pull/698)). 
Waiting for review
- Unsubscribe in push_event leads to API_EventTimeout 
([cppTango#686](https://github.com/tango-controls/cppTango/issues/686), [cppTango#699](https://github.com/tango-controls/cppTango/pull/699))
Requires more investigations.
- Fix 566 const reference parameters ([cppTango#574](https://github.com/tango-controls/cppTango/pull/574)). Waiting for review
- Upgrade llvm in warning as errors CI tests ([cppTango#700](https://github.com/tango-controls/cppTango/pull/700)).

## JTango News


## PyTango News


### Tango meeting 2020

#### Tango Controls Users meeting 2020 contest

## High priorities issues

- [cppTango#686](https://github.com/tango-controls/cppTango/issues/686)

## AOB

### Conda packages

Reynald created [tango-conda-recipes#1](https://github.com/tango-controls/tango-conda-recipes/pull/1) to use Github 
actions to create conda packages and then deploy them easily on the official tango-controls conda channel.
A tango-idl conda package was created as well as a cppTango 9.3.4-rc2 package. 
These conda packages are available as artifacts here: https://github.com/bourtemb/tango-conda-recipes/runs/519928988

Please test it and review the PR.

Improvements will be needed to use tango-controls conda channel instead of conda-forge for the dependencies.

New packages will have to be created for TangoTest, tango_admin, Starter, ...?

### HDB++


### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

The next Tango kernel teleconf meeting will take place in 2 weeks on Thursday 9th April 2020 at 15:00 CEST.

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2020/2020-03-12/Minutes.md#summary-of-remaining-actions)

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

**Action - Soleil**: Implement the fix for events with network aliases.

**Action - S2Innovation**: Create a page in tango-doc where each institute could list the operating systems where cppTango and PyTango are running in their institutes.
It could probably be interesting to list as well the java versions used for the JTango applications.

**Action - volunteers**: Review TangoSourceDistribution PRs.

**Action - cppTango developers and volunteers**: Review the TangoTest PRs.

**Action - S2Innovation**: Create a new cppTango issue to track the problem mentioned while reviewing [cppTango#593](https://github.com/tango-controls/cppTango/pull/593).
 Issue with missing pipe events when RestartServer is called.
 
 **Action - ESRF**: Reynald will send a framadate poll to find a good date for an HDB++ teleconf meeting, 
 since a face to face meeting is discouraged during this period. **Not Done yet because of COVID-19 uncertainties**

## Summary of remaining actions
