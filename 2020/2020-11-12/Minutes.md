# Tango Kernel Follow-up Meeting - 2020/11/12

Held on 2020/11/12 at 15:00 CET on Zoom.

**Participants**:  Marco Bartolini (SKAO), Reynald Bourtembourg, Andrew Goetz (ESRF), Thomas Braun (byte physics), 
Piotr Goryl, Michal Liszcz (S2Innovation), Lorenzo Pivetta (ELETTRA), Sergi Rubio (ALBA)

# Minutes

## Tango RFCs

Please refer to https://github.com/tango-controls/rfc/wiki/Meeting-2020-11-22

Piotr asked how to set/get the list of allowed commands which can still be executed even if a Device is locked.
Are these allowed commands only State and Status?

**Action - S2Innovation (Piotr)**: Contact Emmanuel Taurel to see whether he remembers how to get/set the list of allowed 
commands when a Device is locked.

## Tango Collaboration Meeting
   
A virtual Tango Collaboration Meeting event, similar to the one organized in June 2020 will take place on 17th and 18th November. 

More information and the program is available on https://indico.esrf.fr/indico/event/49

Don't forget to register in advance: https://esrf.zoom.us/meeting/register/tJMkduyvpzkjGdZnmIFIR81jREzUaagWoqPM 

Thomas Braun will be the speaker this time for the C++ core library status presentation.  
There will be a rotation on the cppTango developers to be speaker in the cppTango presentations in the next events.  
Since there has not been many changes since June, this presentation will focus mainly on what we want to achieve in cppTango 9.4.  
Of course there will be slides about the recent 9.3.4 release and Tango webinars.

## Removal of CORBA

A discussion initiated by Andy Goetz took place about the next steps to be able to remove CORBA.  
A good step in cppTango will be to separate public and private headers and refactor the code to get a stable API and ABI not 
impacted by internal refactoring and bugfixes (See [cppTango#735](https://github.com/tango-controls/cppTango/issues/735)).  

The RFCs are now becoming in a state where they could be tested against a prototype.  
So one of the next steps is to work on this prototype and do some iterations over the RFCs to improve them.

It is not clear how much resources will be required to make Tango independent from CORBA but the ideal would be to get 
3 persons working on this topic during several years (3 years?).  

Thomas said pointed out that it is important to continue to improve the current software in parallel with the prototype 
development (and this will require some resources too).

A Call for Tender is almost ready to be sent for a new type of contracts between the Tango Steering Committee and the contractors.  
After a review from the Steering Committee it will be probably published in December.  
These new contracts should allow a company to get a contract to work for Tango over a longer period (up to 3 years).  
Andy will exchange with Marco to get some advices from SKA who is more used to prepare such types of contracts. 
Marco said in SKA they have some contracts which are very easy to extend/renew and they have also the possibility to stop them 
if things don't go well.

## Tango Kernel Webinar

The first Tango Kernel Webinar replay is now available on youtube, but not yet public, only available via the following link
for the moment: https://youtu.be/iIzP4jaQrzw

Please have a look and warn Reynald if you see anything inappropriate in this video (something which should be blurred or cut out).

For the next Tango Kernel Webinars, it was agreed during the meeting to do a cppTango webinar on the event system. 
It was suggested that the best would be to get Emmanuel Taurel presenting it, since he is the original author and 
could share all the secrets of the current event system.

The best would be to get the next Tango Kernel Webinar on Wednesday 9th December at 10:00 am CET.  
Then, ideally, the next Tango Kernel Webinar would take place on the following week on Wednesday 16th December at 10:00 am CET 
and should be presented by Pascal Verdier who will share his knowledge on some of the Tango Kernel projects he has worked on .  
(Astor/Starter, Pogo, JTango?).
These dates are not yet official since we need to ensure the presenters will be available on these dates.

Another idea of Tango Kernel Webinar would be to get Geoff presenting the work done on pybind11 so some other contributors 
could help on this promising project. This webinar could take place in January.  
Andy mentioned that the Tango collaboration could pay for the work provided by Geoff to get this webinar ready.  

## PyTango News

Geoff has been very busy in the last months with other projects and has now no official time to work on pytango-pybind11 project (no contract).  
He will commit all the last changes he did on the pybind11 development branch so some other persons could collaborate 
on this task.  

Geoff mentioned that this code still needs a lot of tiding up (old code commented, ...).

Alba is interested in testing the pybind11 port.

Geoff mentioned that most of the server side tests are passing. The events part is not yet implemented so the the event 
related tests are currently not passing.

Zibi provided some more code to reproduce the issue [pytango#315](https://github.com/tango-controls/pyTango/issues/315).  
It was decided to raise the priority of this issue.

Andy mentioned that a memory leak has been fixed recently in pytango ([pytango#386](https://github.com/tango-controls/pyTango/pull/386)) which was occurring when replicating DeviceProxy 
objects (DeviceInfo part was leaking). Sergi said that he will check whether this fix solves the memory leaks 
issues they were experimenting in some pytango clients at ALBA.

Anton mentioned on kernel slack channel that [pytango#387](https://github.com/tango-controls/pyTango/pull/387) needs 
some cppTango expertise (nothing to do with OmniThread, just the crash).

## cppTango News

### Recent PR merged
PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:

#### tango-9-lts (future 9.4)

- Revise developer documentation ([cppTango#800](https://github.com/tango-controls/cppTango/pull/800))
- Include dependencies as SYSTEM libraries ([cppTango#779](https://github.com/tango-controls/cppTango/pull/779))

#### 9.3 backports

- Backport fix 675 no archive periodic events after polling restart ([cppTango#778](https://github.com/tango-controls/cppTango/pull/778))

### New issues
The following new issues have been created in cppTango since the previous Tango Kernel teleconf meeting:

- Valgrind integration ([cppTango#795](https://github.com/tango-controls/cppTango/issues/795))
- Support forwarded attributes with #dbase=no (better URI parsing) ([cppTango#796](https://github.com/tango-controls/cppTango/issues/796))
- Integration with sanitizers ([cppTango#797](https://github.com/tango-controls/cppTango/issues/797))
- Add CI job with alpine linux ([cppTango#799](https://github.com/tango-controls/cppTango/issues/799))
- Give the possibility to the device server programmer to get information on the client (get_client_ident())... ([cppTango#801](https://github.com/tango-controls/cppTango/issues/801))

### Closed issues

- On performance of JPEG MMX encoder ([cppTango#798](https://github.com/tango-controls/cppTango/issues/798))
- Backport for #704 ([cppTango#774](https://github.com/tango-controls/cppTango/issues/774))
- Docker hub TOS changes ([cppTango#761](https://github.com/tango-controls/cppTango/issues/761))

### Recent developments

The following PRs have been created or updated since last Tango Kernel teleconf:

- On performance of JPEG MMX encoder ([cppTango#798](https://github.com/tango-controls/cppTango/issues/798))
- Event unsubscription from DeviceProxy destructor ([cppTango#746](https://github.com/tango-controls/cppTango/issues/746))
- cppapi/server/jpeg_mmx/jpeg_dct_mmx.cpp: Remove calling GCC internal functions ([cppTango#783](https://github.com/tango-controls/cppTango/issues/783))
- Make it work with 32bit on linux ([cppTango#792](https://github.com/tango-controls/cppTango/issues/792))
- Use chrono to represent log4tango timestamps ([cppTango#794](https://github.com/tango-controls/cppTango/issues/794))
- Attribute classes use incorrect compiler generated special member functions ([cppTango#786](https://github.com/tango-controls/cppTango/issues/786))
- CHANGELOG.md: Update ([cppTango#785](https://github.com/tango-controls/cppTango/issues/785))
- Bugfix/fix abi checking ([cppTango#755](https://github.com/tango-controls/cppTango/issues/755))
- High level C++ API proposal ([cppTango#736](https://github.com/tango-controls/cppTango/issues/736))

### PR merge goals for next meeting
Here is the list of opened PR with "Ready for Merge" label: https://github.com/tango-controls/cppTango/pulls?q=is%3Apr+is%3Aopen+label%3A%22Ready+For+Merge%22

We agreed to set as recurrent goal to review carefully and merge (if approved, of course) the PRs having the "Ready for Merge label" set, 
prioritizing the PR having the "High Priority" label and the external contributions.

Here is the list of PR which were with the "Ready For Merge" label at the time of this teleconf meeting:

- [cppTango#698](https://github.com/tango-controls/cppTango/pull/698) **(high priority)** - Missing 1 approval
- [cppTango#746](https://github.com/tango-controls/cppTango/pull/746) **(High priority)** - Missing 1 approval
- [cppTango#697](https://github.com/tango-controls/cppTango/pull/697) - Changes requested
- [cppTango#703](https://github.com/tango-controls/cppTango/pull/703)
- [cppTango#725](https://github.com/tango-controls/cppTango/pull/725)
- [cppTango#729](https://github.com/tango-controls/cppTango/pull/729)
- [cppTango#737](https://github.com/tango-controls/cppTango/pull/737) - Missing 1 approval
- [cppTango#742](https://github.com/tango-controls/cppTango/pull/742) - Missing 1 approval
- [cppTango#744](https://github.com/tango-controls/cppTango/pull/744) - Has conflict
- [cppTango#746](https://github.com/tango-controls/cppTango/pull/746) - Missing 1 approval
- [cppTango#755](https://github.com/tango-controls/cppTango/pull/755)
- [cppTango#759](https://github.com/tango-controls/cppTango/pull/759) - Missing 1 approval
- [cppTango#766](https://github.com/tango-controls/cppTango/pull/766) - Missing 1 approval
- [cppTango#783](https://github.com/tango-controls/cppTango/pull/783) - Missing 1 approval
- [cppTango#785](https://github.com/tango-controls/cppTango/pull/785)
- [cppTango#790](https://github.com/tango-controls/cppTango/pull/790)
- [cppTango#794](https://github.com/tango-controls/cppTango/pull/794) - Missing 1 approval
- [cppTango#803](https://github.com/tango-controls/cppTango/pull/803)

## JTango News

No news.

## Tango Source Distribution

[TangoSourceDistribution 9.3.4](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4) has been 
released and advertised to the community via the Tango mailing list.

Thomas suggested to avoid providing cppTango patches in the [patches documentation page](https://tango-controls.readthedocs.io/en/latest/installation/patches.html) 
when there is a bug fixed in cppTango as we were doing in the past. 
We will rather provide a new release of cppTango and of the Tango Source Distribution containing the cppTango bug fixed.
The difficulty when preparing a new release is to gather the information on what software parts of the Tango Source 
Distribution should be updated when releasing a new version.  
Reynald suggested to create an issue announcing the preparation of a new release.  
The maintainers of the different software parts of the Tango Source Distribution should comment on this issue if they 
think the software they maintain should be updated in the coming release and they should precise the version that should 
be used.  
For this process to work smoothly, it is important that the different Tango projects maintainers become watchers of the 
TangoSourceDistribution github repository so they would receive notifications when an issue announcing the preparation 
of a new Tango Source Distribution release is created.

Andy tested TDS 9.3.4 on Ubuntu 20.04 and reported some issues with the systemd integration. Andy suggested to add some 
documentation on the README on this topic.

Andy also reported an issue with the retina screen big resolution which is by default making the text on the java applications very small.
There is a trick to work-around this problem playing with GDK_SCALE environment variable. 
It would be good to document this work-around in TDS README too.

**Action - byte physics?**: Document GDB_SCALE trick on Tango Source Distribution README
**Action - byte physics?**: Add some information on Tango Source Distribution README about systemd integration

**Action - Andy?**: Update Documentation to give a recipe on how to install Tango with the Tango Source Distribution on Ubuntu

TDS 9.3.4 has been tested at Elettra on Power PC and Ubuntu 18.04 64 bits. No big issue seen so far.

[Wikipedia Tango page](https://en.wikipedia.org/wiki/TANGO) was still listing Tango 9.2.5 as latest release version.  
Thomas updated the wikipedia page after the meeting to list 9.3.4 as stable release.

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
**Andy tested the installation on Ubuntu 20.04. Elettra tested it on Ubuntu 18.04 64 bits and also on PPC.**

**Action - ESRF (Andy)**: Create an issue (in TangoTickets) to transmit a more meaningful error message when 
Corba Transient Timeout exception are received.

**Action - Sergi**: Check whether the latest Pogo version is fixing an issue regarding dynamic attributes in PyTango High Level API.

**Action - Michal**: Create an issue to keep track of the new jobs we would like to get using quality check tools (clang-tidy, address-sanitizer, thread sanitizer,ubisan, valgrind)
**Done. See [cppTango#795](https://github.com/tango-controls/cppTango/issues/795) and 
[cppTango#797](https://github.com/tango-controls/cppTango/issues/797)**

**Action - Anton**: Create an issue in cpptango for the problem with forwarded attributes when using a file database.
**Done:  See [cppTango#796](https://github.com/tango-controls/cppTango/issues/796)**

**Action - Thomas**: Create News on tango-controls.org website to advertise the 9.3.4 release.
**Thomas said he has submitted a news on tango-controls.org but he does not have the permissions to publish it. 
Someone else has to publish it or Thomas should be granted this permission.**

**Action - Thomas - Reynald**: Update the documentation and the download links to point to latest 9.3.4 Tango distribution.. Reynald should give permission to Thomas on the website.
**Reynald updated the links on the download page.**

## High priorities issues

The priority of ([pytango#315](https://github.com/tango-controls/pytango/issues/315))and 
[pytango#387](https://github.com/tango-controls/pytango/issues/387)) have been raised during the meeting.

Here are the high priority issues defined during the previous meetings and which have not yet been solved:

On PyTango, the priority is on the Windows build (and tests passing on Windows).   
Investigations on why pytango installation problems on Ubuntu 20.04 LTS (https://www.tango-controls.org/community/forum/post/4391) should be done.

The current priorities are: 

- Safe interworking between read_attribute() and push_event() ([cppTango#698](https://github.com/tango-controls/cppTango/issues/698))
- Event subscription lost when destroying different DeviceProxy instance ([pytango#372](https://github.com/tango-controls/pytango/issues/372))
- Exception on unsubscription when a client has two proxies for the same attribute 
([cppTango#353](https://github.com/tango-controls/cppTango/issues/353), [cppTango#746](https://github.com/tango-controls/cppTango/pull/746))
- DS hangs when concurrently subscribing to events and destructing DeviceProxy ([pytango#315](https://github.com/tango-controls/pytango/issues/315))
_ Use OmniThreads in MultiDeviceTestContext ([pytango#387](https://github.com/tango-controls/pytango/issues/387))

## AOB

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

The next Tango kernel Teleconf meeting will take place **in 3 weeks** on Thursday 26th November 2020 at 15:00 **CET**.

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

**Action - ESRF**: Create News on tango-controls.org website to advertise the 9.3.4 release.
**Thomas said he has submitted a news on tango-controls.org but he does not have the permissions to publish it. 
Someone else has to publish it or Thomas should be granted this permission.**

**Action - S2Innovation (Piotr)**: Contact Emmanuel Taurel to see whether he remembers how to get/set the list of allowed 
commands when a Device is locked.

**Action - byte physics?**: Document GDB_SCALE trick on Tango Source Distribution README

**Action - byte physics?**: Add some information on Tango Source Distribution README about systemd integration

**Action - Andy?**: Update Documentation to give a recipe on how to install Tango with the Tango Source Distribution on Ubuntu


