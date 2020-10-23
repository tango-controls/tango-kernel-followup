# Tango Kernel Follow-up Meeting - 2020/10/22

Held on 2020/10/22 at 15:00 CEST on Zoom.

**Participants**:  Marco Bartolini (SKAO), Reynald Bourtembourg (ESRF), Thomas Braun (byte physics), 
Mateusz Celary, Piotr Goryl, Michal Liszcz (S2Innovation), Anton Joubert (SKA-ZA), Jairo Moldes, Sergi Rubio (ALBA)

# Minutes

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2020/2020-10-22/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - Kernel developers**: Look at https://github.com/pulls/review-requested and review/merge pending PRs

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the 
TangoSourceDistribution repository.

**Action - All**: Test [9.3.4](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4) release.
**Thomas tested the Debian package upgrade and is still seeing an issue with the database which is not upgraded as it should.
9.3.4 is in production on 1 ALBA beamline and 5 VMs. No issue so far. 
Sergi reported some deadlocks with Tango 9 when pushing events from threads. 
There is an open issue to attempt to remove the need to use the Tango monitor when pushing events([cpptango#762](https://github.com/tango-controls/cppTango/pull/762)).
cppTango 9.3.4 anf JTango 9.6.6 are in operation since 1 week on the ESRF accelerator control system. 
No problem reported so far but the accelerator was in shutdown. The accelerator is restarting today so big problems (if any) will be seen in the next days.**

**Action - ESRF**: Prepare cpptango 9.4.x conda package based on tango-9-lts branch and upload it to Reyn4ld conda channel 
to ease testing by Anton. **We can remove this action and resurrect it before 9.4 is released.**

**Action - ESRF (Andy)**: Create an issue (in TangoTickets) to transmit a more meaningful error message when 
Corba Transient Timeout exception are received.

**Action - Thomas**: Provide a VM which could be used to witness/debug the Pogo issue with the never-ending splash screen. **Could not reproduce. Issue closed**.

**Action - Sergi**: Check whether the latest Pogo version is fixing an issue regarding dynamic attributes in PyTango High Level API.


## Tango RFCs

Please refer to https://github.com/tango-controls/rfc/wiki/Meeting-2020-10-22

## cppTango News

cppTango 9.3.4 released and marked as latest release on Github.

### Recent PR merged
PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:

#### tango-9-lts (future 9.4)

- Replace sprintf with snprintf ([cppTango#757](https://github.com/tango-controls/cppTango/pull/757)) 
=> Jump from D to B in security in SonarCloud report. 
To go from B to A we have to remove strcat and strcpy invocations (187 occurrences). This will be done.
- INSTALL.md: Add missing cmake options ([cppTango#775](https://github.com/tango-controls/cppTango/pull/775))
- .travis/llvm-latest: Upgrade to llvm 11.0 ([cppTango#777](https://github.com/tango-controls/cppTango/pull/777))
- Fix and document windows build ([cppTango#770](https://github.com/tango-controls/cppTango/pull/770))
- Add more classes to documentation ([cppTango#776](https://github.com/tango-controls/cppTango/pull/776))
- configure/CMakeLists.txt: Remove bogus omniidl check ([cppTango#782](https://github.com/tango-controls/cppTango/pull/782))

#### 9.3 backports

- Add more classes to documentation [backport] ([cppTango#780](https://github.com/tango-controls/cppTango/pull/780))
- CHANGELOG.md: Update [cppTango#785](https://github.com/tango-controls/cppTango/pull/785))

### New issues
The following new issues have been created in cppTango since the previous Tango Kernel teleconf meeting:

- Can not cross-compile to 32bit on x64 debian buster ([cppTango#784](https://github.com/tango-controls/cppTango/pull/784))
- Attribute classes use incorrect compiler generated special member functions ([cppTango#786](https://github.com/tango-controls/cppTango/pull/786)).
- Enforce a minimum zeromq version with cmake ([cppTango#788](https://github.com/tango-controls/cppTango/pull/788)). 
Thomas found a solution which is not requiring pkg_config, so should work on Windows too.
- Does not build in release mode with cmake 3.10 ([cppTango#791](https://github.com/tango-controls/cppTango/pull/791)). 
We should configure a Travis job to use CMake 3.7.

### Closed issues
- Event subscriber exit after device server restart on Windows ([cppTango#501](https://github.com/tango-controls/cppTango/pull/501))

### Recent developments

The following PRs have been created or updated since last Tango Kernel teleconf:

- Backport fix 675 no archive periodic events after polling restart ([cppTango#778](https://github.com/tango-controls/cppTango/pull/778)).
Was already backported. PR kept open to investigate why the tests are failing.
- include dependencies as SYSTEM libraries ([cppTango#779](https://github.com/tango-controls/cppTango/pull/779)). 
The goal of this PR is to silent compilation warnings coming from the external libraries.
- Remove tango has log4tango define ([cppTango#781](https://github.com/tango-controls/cppTango/pull/781)). 
It seems like the code was built to be able to compile/run tango without log4tango but the CMake system currently does not support that.
So we need to clarify whether we should keep this possibility to use tango without log4tango in order to decide whether 
we drop the related code or implement what's missing in the CMake files to support this possibility.
Should be merged after [cppTango#759](https://github.com/tango-controls/cppTango/pull/759).
- Cleanup log4tango ([cppTango#759](https://github.com/tango-controls/cppTango/pull/759)). Additional cleanup suggested by Michal.
- Keep source tree clean and use more targets ([cppTango#766](https://github.com/tango-controls/cppTango/pull/766))
- cppapi/server/jpeg_mmx/jpeg_dct_mmx.cpp: Remove calling GCC internal functions ([cppTango#783](https://github.com/tango-controls/cppTango/pull/783)). 
Michal proposed to do some benchmark tests on his laptop to see whether these MMX optimization are still real optimization.
It was decided to throw away all this assembly code and add an optional dependency to an external libjpeg library. 
(Default would be using this library). If users do not want this optional dependency, 
the few methods used to decode/encode jpeg should throw an exception informing that this feature cannot be used without 
using the libjpeg dependency.
- Remove deprecated functions usage ([cppTango#725](https://github.com/tango-controls/cppTango/pull/725)). 
New travis job linking with clang standard C++ library to ensure we don't use deprecated functions which have been already removed on Mac OS.
1 test is failing because of a Sonar timeout. 
- Musl fixes ([cppTango#787](https://github.com/tango-controls/cppTango/pull/787), [cppTango#767](https://github.com/tango-controls/cppTango/issues/767)). 
Fixes which were required when using musl C library when cross-compiling cppTango on Arm. 
Anton suggested to try with Alpine Linux based docker images which seems to use musl libc. Thomas will try it out.
- Use sonar cache to speed up build ([cppTango#789](https://github.com/tango-controls/cppTango/pull/789)). 
Michal proposes to consider stopping using Sonar and use some open source tools (clang-tidy) to do the same. 
People would be then able to run the static analysis locally. We could also then have more jobs doing different things 
(1 dedicated for code coverage, 1 for regression tests, 1 for quality/static analysis). 
We could also use clang-tidy to do automatic code formatting. We could setup some github actions and provide reports as with artifacts.  
Reynald reminded as well that Michal proposed to use thread sanitizer tool on some tests to track data races and ensure 
some already data races bugs don't come back.
Michal mentioned the address sanitizer tool. It would be useful to have a job running this tool as well and a job with valgrind.
Thomas mentioned ubisan (Undefined behaviour sanitizer) and said it would be useful to gat a job with this tool too.

**Action - Michal**: Create an issue to keep track of the new jobs we would like to get using quality check tools (clang-tidy, address-sanitizer, thread sanitizer,ubisan, valgrind)

- log4tango: Fix the check for int64_t ([cppTango#765](https://github.com/tango-controls/cppTango/pullwith/765)).
Michal proposed to remove that type and replace it with chrono::steady_clock. Michal will check whether this type is used only internally or not.
- configure/CMakeLists.txt: Enforce a minimum libzmq version ([cppTango#790](https://github.com/tango-controls/cppTango/pull/790))
- Make it work with 32bit on linux ([cppTango#792](https://github.com/tango-controls/cppTango/pull/792))

### PR merge goals for next meeting
Here is the list of opened PR with "Ready for Merge" label: https://github.com/tango-controls/cppTango/pulls?q=is%3Apr+is%3Aopen+label%3A%22Ready+For+Merge%22

We agreed to set as recurrent goal to review carefully and merge (if approved, of course) the PRs having the "Ready for Merge label" set, 
prioritizing the PR having the "High Priority" label and the external contributions.

Here is the list of PR which were with the "Ready For Merge" label at the time of this teleconf meeting:

- [cppTango#698](https://github.com/tango-controls/cppTango/pull/698) **(high priority)** - Missing 1 approval
- [cppTango#746](https://github.com/tango-controls/cppTango/pull/746) **(High priority)** - Missing 1 approval
- [cppTango#697](https://github.com/tango-controls/cppTango/pull/697) - Changes requested
- [cppTango#703](https://github.com/tango-controls/cppTango/pull/703)
- [cppTango#729](https://github.com/tango-controls/cppTango/pull/729)
- [cppTango#737](https://github.com/tango-controls/cppTango/pull/737) - Missing 1 approval
- [cppTango#742](https://github.com/tango-controls/cppTango/pull/742) - Missing 1 approval
- [cppTango#744](https://github.com/tango-controls/cppTango/pull/744) - Has conflict
- [cppTango#759](https://github.com/tango-controls/cppTango/pull/759) - Missing 1 approval
- [cppTango#766](https://github.com/tango-controls/cppTango/pull/766) - Missing 1 approval
- [cppTango#779](https://github.com/tango-controls/cppTango/pull/779) - Missing 1 approval
- [cppTango#783](https://github.com/tango-controls/cppTango/pull/783)
- [cppTango#785](https://github.com/tango-controls/cppTango/pull/785)
- [cppTango#790](https://github.com/tango-controls/cppTango/pull/790)

## JTango News

No news.

## PyTango News

Mateusz solved an issue with the DeviceTestContext (file handler was not closed correctly).

Mateusz rewrote some tests using pytest-xprocess library instaed of the DeviceTestContext. 
He rewrote 3 tests over 4.  
2 of them are ok now. There is an issue with the 3rd one where the event subscriptions ids are incrementing after restarting the tests.

Anton suggested to meet Mateusz in a separate meeting.

Anton reported an issue he discovered with forwarded attributes when using a file database. 
There is something wrong in the parsing of the attribute name in cpptango.

**Action - Anton**: Create an issue in cpptango for the problem with forwarded attributes when using a file database.

Anton reported that someone commented about a memory leak issue which is already fixed in pybind11 branch. 
Some effort should be done to try to fix this memory leak as well in the current non-pybind11 development branch because we don't know the release date for the pybind11 release.

Anton is interested in improving the CI in order to be able to more easily deploy newer versions of pytango onto pypi. 
This should ease the process to make a new release and reduce the number of manual steps.

Sergi will ask Tiago whether he could spend some time on testing pybind11 and have a look at it. 
The branches have diverged a lot so it will be very difficult to merge them.

## Tango Source Distribution

[TangoSourceDistribution 9.3.4](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4) has been 
released and advertised to the community via the Tango mailing list.

**Action - Thomas**: Create News on tango-controls.org website to advertise the 9.3.4 release.

**Action - Thomas - Reynald**: Update the documentation and the download links to point to latest 9.3.4 Tango distribution.. Reynald should give permission to Thomas on the website.

For 9.4 TDS release, Thomas suggested to move everything to CMake.

## High priorities issues

No new high priority issues have been raised during the meeting by the different institutes.

Here are the high priority issues defined during the previous meetings and which have not yet been solved:

On PyTango, the priority is on the Windows build (and tests passing on Windows).   
Investigations on why pytango installation problems on Ubuntu 20.04 LTS (https://www.tango-controls.org/community/forum/post/4391) should be done.

The others priorities are: 

- Safe interworking between read_attribute() and push_event() ([cppTango#698](https://github.com/tango-controls/cppTango/issues/698))
- Event subscription lost when destroying different DeviceProxy instance ([pytango#372](https://github.com/tango-controls/pytango/issues/372))
- Exception on unsubscription when a client has two proxies for the same attribute 
([cppTango#353](https://github.com/tango-controls/cppTango/issues/353), [cppTango#746](https://github.com/tango-controls/cppTango/pull/746))

## Tango Kernel Webinar

It has been decided to postpone the Tango Kernel training webinar to Tuesday 3rd November 9:00 am CET to give more time to the 
participants to be aware of it and to prepare it.

Thomas suggested to ask to the participants to try to compile cpptango on their own before attending the Kernel webinar 
and Sergi proposed to mention that in the advertising.

The first Tango Kernel training webinar will take place on Monday 9th November  at 9:00 am CET. It will last about 90 minutes.
Please refer to the following link to get the corresponding time in the different areas of the world (Thanks, Marco for the link): 
https://www.timeanddate.com/worldclock/meetingdetails.html?year=2020&month=11&day=3&hour=8&min=0&sec=0&p1=302&p2=37&p3=196&p4=31&p5=195&p6=240&p7=56&p8=1038

We'll try to organize 1 webinar per month.

The first webinar will present an overview of the cppTango code and how to contribute. 
Here is the outline:

1. Introduction (Reynald)
2. cppTango repository overview (Reynald)
    - Main branches
    - Contributions rules (Reviews, Checks)
3. CppTango dependencies (Reynald)
    - cppTango and CORBA (IDL file introduction + stubs generation mechanism) (Reynald)
    - Why do we have dependencies to omniORB, zmq, cppzmq and tango-idl? (Reynald)
4. How to compile cppTango? (Thomas)
    - How to install the dependencies (omniORB, zmq, cppzmq, tango-idl)?
    - Compilation flags
    - How to compile cppTango and the tests?
    - How to compile on Windows?
5. How to run the tests? (Thomas)
6. How to add a new test? (Thomas)
7. Architecture overview (Michal)
    - Short description of the main classes and their interactions (Some diagrams + browsing the code)
8. Practical example : Code navigation. What happens when an attribute is read? (Michal)
    * Debugging demo and code navigation
    * Debugging tricks
9. Questions (~30 minutes)

## AOB
### Tango Collaboration Meeting
   
A virtual Tango Collaboration Meeting event, similar to the one organized in June 2020 will take place on 17th and 18th November. 

More information on https://indico.esrf.fr/indico/event/49

Piotr proposed to try to find a way to organize some virtual coffee breaks during this meeting.

For cppTango news, a 20 minutes presentation time slot should be good. There are no big changes since June 
so we could also talk about the future and the 9.4 release as well.

### Conda packages

Reynald created a PR to create cpptango 9.3.4 conda package.  
The package still needs to be uploaded on tango-controls conda channel.

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

The next Tango kernel Teleconf meeting will take place **in 3 weeks** on Thursday 12th November 2020 at 15:00 **CET**.

## Summary of remaining actions

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - Kernel developers**: Look at https://github.com/pulls/review-requested and review/merge pending PRs

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the 
TangoSourceDistribution repository.

**Action - All**: Test [9.3.4](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4) release.

**Action - ESRF (Andy)**: Create an issue (in TangoTickets) to transmit a more meaningful error message when 
Corba Transient Timeout exception are received.

**Action - Sergi**: Check whether the latest Pogo version is fixing an issue regarding dynamic attributes in PyTango High Level API.

**Action - Michal**: Create an issue to keep track of the new jobs we would like to get using quality check tools (clang-tidy, address-sanitizer, thread sanitizer,ubisan, valgrind)

**Action - Anton**: Create an issue in cpptango for the problem with forwarded attributes when using a file database.

**Action - Thomas**: Create News on tango-controls.org website to advertise the 9.3.4 release.

**Action - Thomas - Reynald**: Update the documentation and the download links to point to latest 9.3.4 Tango distribution.. Reynald should give permission to Thomas on the website.
