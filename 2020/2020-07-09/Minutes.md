# Tango Kernel Follow-up Meeting - 2020/07/09

Held on 2020/07/09 at 15:00 CEST on Zoom.

Participants:  Andrew Goetz, Reynald Bourtembourg (ESRF), Anton Joubert (SKA-ZA), 
Michal Liszcz, Wojciech Kitka (S2Innovation), Thomas Braun (byte physics)

# Minutes

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2020/2020-06-11/Minutes.md#summary-of-remaining-actions)

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
Gwenaelle has found a bug. WIP.

**Action - ESRF**: Prepare cpptango 9.4.x conda package based on tango-9-lts branch.
**Some conda cpptango and tango-test conda packages using cppTango tango-9-lts branch have been generated and can be 
downloaded on https://github.com/tango-controls/tango-conda-recipes/actions/runs/164651901**

## cppTango News

### Recent PR merged
PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:

#### tango-9-lts (future 9.4)

- Require C++14 standard ([cppTango#732](https://github.com/tango-controls/cppTango/pull/732))
- Use map for attribute lookup in MultiAttribute::check_associated ([cppTango#564](https://github.com/tango-controls/cppTango/pull/564),
 [cppTango#556](https://github.com/tango-controls/cppTango/pull/556))

#### 9.3 backports

- Use map for attribute lookup in MultiAttribute::check_associated  ([cppTango#738](https://github.com/tango-controls/cppTango/pull/738),
 [cppTango#556](https://github.com/tango-controls/cppTango/pull/556))

### New issues
The following new issues have been created in cppTango since the previous Tango Kernel teleconf meeting:

- Try out github actions to replace appveyor ([cppTango#731](https://github.com/tango-controls/cppTango/issues/731))
- Use CMake built-in support for precompiled headers ([cppTango#733](https://github.com/tango-controls/cppTango/issues/733)) 
CLOSED but might be reopened in the future.
- -Winvalid-pch in Debian 10 Release job ([cppTango#734](https://github.com/tango-controls/cppTango/issues/734))
- Public/private header separation and stable ABI proposal ([cppTango#735](https://github.com/tango-controls/cppTango/issues/735))
- High level C++ API proposal ([cppTango#736](https://github.com/tango-controls/cppTango/issues/736))
- Potential crash when a device is locked using Device Lock feature and is receiving a client request from another 
device exported by the same device server ([cppTango#739](https://github.com/tango-controls/cppTango/issues/739))

### Recent developments

Michal has started the work on the following PR:
- Restore event subscriptions after device server rename and restart ([cppTango#737](https://github.com/tango-controls/cppTango/pull/737), [cppTango#679](https://github.com/tango-controls/cppTango/issues/679))

Michal has created the 2 following issues to trigger discussions: 
- Public/private header separation and stable ABI proposal ([cppTango#735](https://github.com/tango-controls/cppTango/issues/735))
- High level C++ API proposal ([cppTango#736](https://github.com/tango-controls/cppTango/issues/736))

Thomas has been working on a PR to remove deprecated C++ code ([cppTango#725](https://github.com/tango-controls/cppTango/pull/725)).

He has also been working on making sonarcloud work again.

Thomas is currently working on omniORB 4.3 tests and will add a dedicated Travis job for this version.

There is still an issue with the automatic ABI/API compliance check. Thomas is working on that.
Michal suggested to find a way to point the tool to our headers.

### PR Merge goals from last meeting
Here is the list of PR which were with the "Ready For Merge" label at the time of the previous teleconf meeting:

- [cppTango#698](https://github.com/tango-controls/cppTango/pull/698) (high priority) - **Missing 1 approval**
- [cppTango#721](https://github.com/tango-controls/cppTango/pull/721) **Missing 1 approval**
- [cppTango#703](https://github.com/tango-controls/cppTango/pull/703) **Missing 1 approval**
- [cppTango#697](https://github.com/tango-controls/cppTango/pull/697)
- [cppTango#574](https://github.com/tango-controls/cppTango/pull/574) **Missing 1 approval**
- [cppTango#564](https://github.com/tango-controls/cppTango/pull/564) **Merged**
- [cppTango#730](https://github.com/tango-controls/cppTango/pull/730)
- [cppTango#724](https://github.com/tango-controls/cppTango/pull/724) **Missing 1 approval**
- [cppTango#715](https://github.com/tango-controls/cppTango/pull/715) **Closed - already merged via #662**
- [cppTango#704](https://github.com/tango-controls/cppTango/pull/704) **Missing 1 approval**

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

**Action - ESRF (Andy)**: Create an issue (in TangoTickets) to transmit a more meaningful error message when 
Corba Transient Timeout exception are received.

## JTango News

Gwenaelle Abeille and Pascal Verdier have been working on fixing the bug with the heartbeat events (See ([jtango#104](https://github.com/tango-controls/jtango/pull/104)).

## PyTango News

Wojciech Kitka has done some progress on the Windows build issue. 
He encountered problems with pytest which is forking subprocesses which are not supported on Windows.
He is working on a solution.

pyTango tests are now passing with python 3.8 on Travis CI.

New issues have been reported:

- Event subscription lost when destroying different DeviceProxy instance ([pytango#372](https://github.com/tango-controls/pytango/issues/372))
- Concurrently executing a command and pushing event leads to dead lock ([TangoTickets#39](https://github.com/tango-controls/TangoTickets/issues/39))

**Action - ESRF**: Create a pytango conda package for python 3.8. 
**Done. This package is available on tango-controls conda channel**

## Tango Source Distribution

No news since last meeting.

## Conda packages

cpptango 9.3.4-rc6, tango-test and pytango 9.3.2 linux-64 conda packages are available on tango-controls conda channel.

cpptango 9.4 beta version conda package 
(([tango-conda-recipes#7](https://github.com/tango-controls/tango-conda-recipes/pull/7)). 
Reynald has done some work on that and managed to generate packages using Github workflow.
Please refer to https://github.com/tango-controls/tango-conda-recipes/pull/8 github workflow artifacts.

## High priorities issues

On PyTango, the priority is on the Windows build (and tests passing on Windows).

The others priorities are: 

- Conda package with support for Python3.8 [pytango#346](https://github.com/tango-controls/pytango/issues/346))
- Safe interworking between read_attribute() and push_event() ([cppTango#698](https://github.com/tango-controls/cppTango/issues/698))
- Event subscription lost when destroying different DeviceProxy instance ([pytango#372](https://github.com/tango-controls/pytango/issues/372))
- Exception on unsubscription when a client has two proxies for the same attribute ([cppTango#353](https://github.com/tango-controls/cppTango/issues/353))

## AOB

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

Reynald and Andy at least won't be available in 2 weeks (Thursday 23rd July).
If Tango kernel developers wish to meet, they can if they want, using the same Zoom link as for the last Tango Kernel 
Teleconf Meeting, else the next Tango kernel Teleconf meeting will take place on Thursday 13th August 2020 at 15:00 CEST.

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

**Action - ESRF**: Prepare cpptango 9.4.x conda package based on tango-9-lts branch.

**Action - ESRF (Andy)**: Create an issue (in TangoTickets) to transmit a more meaningful error message when 
Corba Transient Timeout exception are received.