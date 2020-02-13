# Tango Kernel Follow-up Meeting - 2020/02/13

Held on 2020/02/13 at 15:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants:  Reynald Bourtembourg (ESRF), Jairo Moldes (ALBA), Anton Joubert (SKA-ZA),
               Igor Khokhriakov (IK), Goeffrey Mant(STFC), Michal Liszcz (S2Innovation)

# Minutes

## Tango Source Distribution

Thomas Braun implemented the changes suggested during the last Tango Kernel teleconf meeting.
He created [TangoSourceDistribution#69](https://github.com/tango-controls/TangoSourceDistribution/issues/69) and [TangoSourceDistribution#70](https://github.com/tango-controls/TangoSourceDistribution/issues/70).
These Pull requests need to be tested and approved. Reviewers are welcome.

**Action - volunteers**: Review TangoSourceDistribution PRs.

## cppTango News

### Current developments
- Discussion on how to fix [cppTango#401](https://github.com/tango-controls/cppTango/issues/401). 
In particular, what should we do if a user wants to change the max value attribute property of a memorized attribute and when the new max value is below the current attribute set point (which is memorized)?

It has been decided during the meeting to fix the bug reported in [cppTango#401](https://github.com/tango-controls/cppTango/issues/401) 
when setting the max alarm threshold and to keep the current behaviour when changing the max value of memorized attributes 
(throwing an exception when trying to  change the max value with a value which is below the current memorized attribute set point).
Please do not hesitate to share your opinion on the Github issue if you consider this as a problem. 

Michal suggested to have a look at Gihub actions feature to replace the appveyor builds which are very slow.

### Recent PR merged
Several PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:
- Fix race conditions between polling threads and user threads pushing events [#641](https://github.com/tango-controls/cppTango/pull/641) and [#665](https://github.com/tango-controls/cppTango/pull/665)
- Backport: Avoid undefined interface warning msvc [#664](https://github.com/tango-controls/cppTango/pull/664)
- Add switch to disable building MMX [#674](https://github.com/tango-controls/cppTango/pull/674) (9.3-backports)
- Fix memory leak in Attribute::get_att_device_class() [#677](https://github.com/tango-controls/cppTango/pull/677) and [#678](https://github.com/tango-controls/cppTango/pull/678)
- Travis: remove deprecated skip_cleanup [#682](https://github.com/tango-controls/cppTango/pull/682) and [#683](https://github.com/tango-controls/cppTango/pull/683)

### New issues
The following issues and pull requests have been created since the last teleconf meeting and are not yet solved:

- Fix sonar scanner invocation [#666](https://github.com/tango-controls/cppTango/issues/666)
- Prepare 9.3.4-rc4 [#667](https://github.com/tango-controls/cppTango/issues/667)
- CMakeLists.txt: Add option to disable building the test suite [#669](https://github.com/tango-controls/cppTango/pull/668)
- appveyor.yml: Fail jobs faster [#669](https://github.com/tango-controls/cppTango/issues/669)
- Add switch to disable building tests [#670](https://github.com/tango-controls/cppTango/issues/670)
- Switch to python3 for tests [#673](https://github.com/tango-controls/cppTango/issues/673)
- Archive periodic events no longer received after polling restart [#675](https://github.com/tango-controls/cppTango/issues/675)
- Event reconnection issue after renaming a device server instance [#679](https://github.com/tango-controls/cppTango/issues/679)
- Event data corruption [#684](https://github.com/tango-controls/cppTango/issues/684). 
A Pull request has been proposed to fix this issue  [#685](https://github.com/tango-controls/cppTango/pull/685)

## JTango News

No news from Soleil since the last meeting about the fix for the events not working all the time when using Tango hosts with network aliases.

## PyTango News

- Issue [#292](https://github.com/tango-controls/pytango/issues/292) related to `__del__` and `DeviceProxy` destructor deadlock:  making good progress.
- A new release should be made soon - there are some useful additions.
- No big progress on pybind11 since the last meeting. 
Code is available on [pybind11 branch](https://github.com/tango-controls/pytango/tree/pybind11) from PyTango repository.
Geoff will update this branch as soon as there will be new pybind11 related development progress. 

## High priorities issues

No new critical issue raised.

## AOB

### Tango meeting in Russia

Registration for the meeting is now open! Please proceed to the event's Indico page for more information: [link](https://indico.esrf.fr/indico/event/41/).
Please do not wait too much to book the plane tickets and hotel because there are some other big events taking place in 
 Saint Petersburg during the same period as the Tango meeting.

### Conda packages

Reynald got in touch with Tiago who provided the links to the gitlab repository where the conda recipe is present.
Reynald suggests to store the conda recipes on tango-controls github organization and to create more conda packages with a finer granularity.
For instance, one package with only the tango c++ library, one package for the Tango starter, etc...
Reynald played a bit with Github actions and thinks this kind of repositories would be a good candidate to start using Github actions.

**Action - ESRF**: Move conda recipes to a new repository in tango-controls Github organization.

### TangoTest improvements 

The 2 open issues from TangoTest repositories have been addressed in some Pull Requests by Thomas Braun (byte physics) 
and Katarzyna Rzęsikowska (S2Innovation). They now need to be reviewed and approved.

**Action - cppTango developers and volunteers**: Review the TangoTest PRs.

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET (Paris time).

The next Tango kernel teleconf meeting will take place in 2 weeks on Thursday 27th February 2020 at 15:00 CET.

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2020/2020-01-23/Minutes.md#summary-of-remaining-actions)

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

**Action - S2Innovation**: Piotr said he will take care of the documentation issues reported while preparing this 9.3.4 
Tango source distribution release.
Piotr will also update the Tango documentation to add links to rpm files created/used by Max IV.
**New issues have been created on tango-doc repository to keep track of these issues.**

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could
use tango-controls.

**Action - Soleil**: Implement the fix for events with network aliases. **No News since the last teleconf meeting**

**Action - Nexeya**: Comment [cppTango#656](https://github.com/tango-controls/cppTango/issues/656). **Done: Sébastien Gara commented the issue**

**Action - byte physics**: Display a warning in the summary appearing at the end of _configure_ script execution if libmariadb2 is detected.
 **[TangoSourceDistribution#69](https://github.com/tango-controls/TangoSourceDistribution/pull/69) has been created and needs to be reviewed.**

**Action - ESRF**: Contact Tiago to get information on how to create a new official tango-controls conda package and find a way to automate/simplify this process.
**Tiago replied and gave all the needed information**.

**Action - S2Innovation?**: Create a page in tango-doc where each institute could list the operating systems where cppTango and PyTango are running in their institutes.
It could probably be interesting to list as well the java versions used for the JTango applications.

## Summary of remaining actions

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

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could
use tango-controls.

**Action - Soleil**: Implement the fix for events with network aliases.

**Action - S2Innovation?**: Create a page in tango-doc where each institute could list the operating systems where cppTango and PyTango are running in their institutes.
It could probably be interesting to list as well the java versions used for the JTango applications.

**Action - volunteers**: Review TangoSourceDistribution PRs.

**Action - ESRF**: Move conda recipes to a new repository in tango-controls Github organization.

**Action - cppTango developers and volunteers**: Review the TangoTest PRs.
