# Tango Kernel Follow-up Meeting - 2020/06/25

Held on 2020/06/25 at 15:00 CEST on Zoom.

Participants:  Andrew Goetz, Reynald Bourtembourg (ESRF), Sergi Rubio (ALBA), Anton Joubert (SKA-ZA), Lorenzo Pivetta (ELETTRA),
 Michal Liszcz (S2Innovation), Thomas Braun (byte physics), Geoffrey Mant (STFC)

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
**WIP. 
https://github.com/tango-controls/tango-doc/pull/344 and https://github.com/tango-controls/tango-doc/pull/345 already merged.**

**Action - Soleil**: Fix last issues with events in JTango and release a new JTango version which will be used in the next Tango Source Distribution release.

**Action - SKA-ZA**: Create an issue in TangoTickets for the issue seen in Kubernetes.  
**Done: https://github.com/tango-controls/TangoTickets/issues/38 
A new approach will be taken (only 1 container per pod). It was decided that this ticket can be closed with an 
explanation of the work-around used by SKA.**

## cppTango News

cppTango 9.3.4-rc6 is installed at Elettra on PPC platform (at least).  
cppTango 9.3.4-rc6 is installed and in operation at the ESRF on the accelerator control system. 
The accelerator was restarting today so if there are some critical issues with the new version, they should be 
discovered in the coming days.

### Recent PR merged
1 PR has been merged since the last meeting.
Here is a list of improvements and bug fixes:

#### tango-9-lts (future 9.4)

- Automate abi api compliance check ([cppTango#662](https://github.com/tango-controls/cppTango/pull/662))

#### 9.3 backports

No PR merged since last meeting.

### New issues
No new issue reported in cppTango since the previous Tango Kernel teleconf meeting.

### Recent developments

Michal has been working on a PR involving timestamps. He created a new test which is using some std chrono C++14 features.
Since it was planned to require C++14 standard around August 2020 for tango-9-lts branch and since no 9.4 official version has been released yet, 
it was been decided during today's meeting to require C++14 in the tango-9-lts branch from now on.  
Michal said it is better to have the tests and the Tango core code using the same C++ standard requirements.  
Lorenzo pointed out that this move to C++14 will make the bug fixing backport job more complicated and will imply fixing 
the bugs with 2 different implementations in some situations.  
This risk is understood and the advantages of using some standard features justify this policy change for the 
tango-9-lts branch and should improve its maintainability and hopefully its reliability too.
Thomas pointed out that he made some investigations and realized that VS2015 does not implement all the C++14 standard features.  
He also said that code built from VS2017/2019 is binary compatible with VS2015. So basically, we could drop 
support for VS2015 if we wish so, see [here](https://docs.microsoft.com/en-us/cpp/porting/binary-compat-2015-2017?view=vs-2019).
It was decided to authorize the usage of C++14 standard features in tango-9-lts branch, only if these features are 
supported by VS2015. If the need arises to use a C++14 feature not supported by VS2015, then we will reconsider the 
continuity of VS2015 support in tango-9-lts branch.
Thomas provided this link to a page showing the features implemented in the different VS versions:  
https://docs.microsoft.com/en-us/cpp/overview/visual-cpp-language-conformance?view=vs-2019

Michal proposed a new PR ([cppTango#729](https://github.com/tango-controls/cppTango/pull/729)) to use std::chrono in 
polling calculations. He will investigate the failure of the tests on Debian 8.

Michal will also work on [cppTango#679](https://github.com/tango-controls/cppTango/issues/679) (Event reconnection issue 
after renaming a device server instance) in the coming weeks.

Thomas has been working on making Sonar Cloud and Coveralls working again ([cppTango#726](https://github.com/tango-controls/cppTango/issues/726)).
Sonar cloud issue is already fixed but there is still some work to be done for coveralls.

Thomas has also been working on a PR to remove references to MSVC < 14 in tango-9-lts CMake files ([cppTango#724](https://github.com/tango-controls/cppTango/issues/724))

Thomas also worked on [cppTango#715](https://github.com/tango-controls/cppTango/issues/715) 
(configure/CMakeLists.txt: Use dpkg-buildflags flags for builds) which is now ready for merge.

Thomas is making progress in removing std::binary_function usage in the code ([cppTango#680](https://github.com/tango-controls/cppTango/issues/680)).

Thomas also made some tests for the appveyor artifacts auto-upload when a new tag is created.

Thomas said it would be better to create an appveyor tango-controls or cpptango organization instead of having 3 
different accounts as now which can be used to execute the appveyor builds.

Michal asked whether we could replace appveyor with github actions. Thomas will have a look at this possibility 
([cppTango#731](https://github.com/tango-controls/cppTango/issues/731)).

Andy asked whether using std::chrono could support nanosecond precision. Michal said that indeed it should be no problem 
to support timestamps with nano second precision using std::chrono standard features but some things won't be changed 
like the polling period configuration resolution (ms) for instance. Michal also said that the existing code which is putting zeros in 
the nanoseconds part of the timestamps could be changed to get a relevant nanosecond precision.

### PR Merge goals from last meeting
Here is the list of PR which were with the "Ready For Merge" label at the time of the previous teleconf meeting:

- [cppTango#698](https://github.com/tango-controls/cppTango/pull/698) (high priority) - **Missing 1 approval**
- [cppTango#685](https://github.com/tango-controls/cppTango/pull/685) (external contribution) - changes requested
- [cppTango#721](https://github.com/tango-controls/cppTango/pull/721) **Missing 1 approval**
- [cppTango#703](https://github.com/tango-controls/cppTango/pull/703) **Missing 1 approval**
- [cppTango#697](https://github.com/tango-controls/cppTango/pull/697)
- [cppTango#574](https://github.com/tango-controls/cppTango/pull/574) **Missing 1 approval**
- [cppTango#564](https://github.com/tango-controls/cppTango/pull/564) **Missing 1 approval**

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
- [cppTango#564](https://github.com/tango-controls/cppTango/pull/564) **Missing 1 approval**
- [cppTango#730](https://github.com/tango-controls/cppTango/pull/730)
- [cppTango#724](https://github.com/tango-controls/cppTango/pull/724)
- [cppTango#715](https://github.com/tango-controls/cppTango/pull/715)
- [cppTango#704](https://github.com/tango-controls/cppTango/pull/704)

## JTango News

No news since last meeting.

## PyTango News

Wojciech Kitka has done some progress on the Windows build issue. 
He will try to execute the PyTango tests to check whether it is working as expected.

Geoff reported that for the pybind11 development branch, all the server tests are passing but he is facing an issue 
with MultiDeviceContext which is required to execute the other tests and this class does not work yet correctly in 
pybind11 development branch.
Once this is working as expected, Geoff will concentrate on the difficult task of merging his changes with the latest 
pytango development branch. He should have some time to work on pybind11 in a couple of weeks.

Sergi added that Alba needs to have all the tests passing correctly in order to be able to test the pybind11 beta version.

Sergi is investigating on a memory leak detected with one of their device servers.  
The origin of the leak is still unclear (device server or pytango/cpptango?).

## Tango Source Distribution

A new issue for 9.3.4-rc7 preparation has been created.
The POGO version will be frozen since new versions require Java >= 11.

## Conda packages

Reynald worked on cpptango 9.3.4-rc6 and tango-test conda packages. He will merge the PR and make the packages available 
on tango-controls conda channel.
These new versions allowed to build new pytango conda packages for python 2.7, 3.5, 3.6 and 3.7 but some tests are 
failing on python 3.5. Anton will investigate on this tests failure.

Sergi said that Carlos Pascual who has a good experience in packaging software is volunteer in helping building pytango 
conda packages. Thanks Carlos!

Anton said that he would like to get a cpptango 9.4 beta version conda package 
(([tango-conda-recipes#7](https://github.com/tango-controls/tango-conda-recipes/pull/7)). 
Reynald will work on that.

**Action - ESRF**: Prepare cpptango 9.4.x conda package based on tango-9-lts branch.

## High priorities issues

On PyTango, the priority is on the Windows build (and tests passing on Windows).

The others priorities are still the same ones as the ones which were defined in the last meeting:

PyTango conda packages ([pytango-conda-recipes#1](https://github.com/tango-controls/pytango-conda-recipes/pull/1) ,
[pytango#346](https://github.com/tango-controls/pytango/issues/346))

- appveyor: Add support for automatic uploading of releases to github ([cppTango#602](https://github.com/tango-controls/cppTango/issues/602))
- Safe interworking between read_attribute() and push_event() ([cppTango#698](https://github.com/tango-controls/cppTango/issues/698))

Reynald would like to draw more attention on [cppTango#679](https://github.com/tango-controls/cppTango/issues/679) 
(Event reconnection issue after renaming a device server instance).

## AOB

### HDB++

The next HDB++ teleconference meeting will take place on Friday 26th June at 14:00 CEST.

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

The next Tango kernel teleconf meeting will take place in 2 weeks on Thursday 9th July June 2020 at 15:00 CEST.

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
