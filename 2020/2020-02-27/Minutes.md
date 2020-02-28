# Tango Kernel Follow-up Meeting - 2020/02/27

Held on 2020/02/27 at 15:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants:  Andrew Goetz, Reynald Bourtembourg (ESRF), Jairo Moldes, Sergi Rubio (ALBA), Anton Joubert (SKA-ZA),
               Geoffrey Mant(STFC), Michal Liszcz (S2Innovation), Thomas Braun (byte physics)

# Minutes

## Tango Source Distribution

No progress since the last teleconference. 
Waiting for reviews of several issues in TangoSourceDistribution and cppTango repositories to be able to release 9.3.4-rc4

Andy mentioned that the size of the Tango Source Distribution package is now much bigger than it used to be 
(compared to 9.2.5a version for instance).
This is mainly due to the images and presentation which are provided with the documentation.
Since very few users will rely on this offline documentation (most of the users are reading the online documentation on 
readthedocs), it might be interesting to create a lighter tango source distribution package and to provide the 
documentation in a separate package.
We need to see with Frédéric Picca whether this would be OK to prepare the official Tango Debian packages.

Alba is currently deploying Tango 9.3.4-rc2. They had an issue with some wrong permissions in /tmp on their computers.
omniorb needs to be able to create files and directories under /tmp to work properly.

## cppTango News

### Recent PR merged
Several PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:
- Add switch to disable mmx build lts [cppTango#676](https://github.com/tango-controls/cppTango/pull/676)
- appveyor.yml: Fail jobs faster [cppTango#669](https://github.com/tango-controls/cppTango/pull/669)

### New issues
The following issues and pull requests have been created since the last teleconf meeting and are not yet solved:
- Unsubscribe in push_event leads to API_EventTimeout [cppTango#686](https://github.com/tango-controls/cppTango/issues/686)
- Fix omniidl error checks [cppTango#687](https://github.com/tango-controls/cppTango/pull/687)
- Shared/static switching on Windows [cppTango#688](https://github.com/tango-controls/cppTango/pull/688)

## JTango News

Pascal Verdier fixed [JTango#100](https://github.com/tango-controls/JTango/issues/100) (Device Proxy Timeout is 
overwritten after a re-connection). The fix will be available in the next release.

A new release will come after the fix for the heartbeat events problems will be fully implemented.
Gwenaelle should get some time to work on that issue during the week from 9th to 13th March.

## PyTango News

[pytango#333](https://github.com/tango-controls/pytango/issues/333) raised the question whether the Green Mode is still 
experimental and whether we should continue to maintain 3 different modes (green mode, asyncio and concurrent.future).

Sergi would like to push for keeping asyncio and concurrent.future. He thinks asyncio is the most used and concurrent.future is promising.

Andy said that green mode is in production at the ESRF and the new BLISS framework for the ESRF beamlines control is heavily 
using the green mode.

Geoff has been using gevents since a while without problem but also mentioned that he also did the exercise to replace 
gevent code with asyncio code and it is working fine too.

The documentation should be updated to mention that asyncio should be the preferred way and that the green mode is not experimental.

We have to see whether we continue maintaining all these different modes because this is additional work for the 
maintainers and there could be discrepancies between the different implementations as already noticed recently with the 
is_allowed methods not being called in async mode [pytango#173](https://github.com/tango-controls/pytango/issues/173).

Geoff reported that there has been some progress on the migration to pybind11.
The standard PyTango tests for the client part are now fully working and passing.

Geoff and Anton will work together to fix the current merging conflicts in pybind11 branch which are preventing the 
Travis tests from being executed.

## High priorities issues

cppTango high priorities issues have the high priority label.
Here is the list of the currently opened high priority cppTango issues and PR: https://github.com/tango-controls/cppTango/labels/high%20priority :
- [cppTango#689](https://github.com/tango-controls/cppTango/pull/689)
- [cppTango#686](https://github.com/tango-controls/cppTango/issues/686)
- [cppTango#672](https://github.com/tango-controls/cppTango/pull/672)
- [cppTango#667](https://github.com/tango-controls/cppTango/issues/667)
- [cppTango#616](https://github.com/tango-controls/cppTango/pull/616)
- [cppTango#573](https://github.com/tango-controls/cppTango/pull/573)

In JTango, the fix for the events heartbeats is the most urgent because it is required before making a new release.

## AOB

### Conda packages

Tango Conda recipes have been moved/copied to a new repository in tango-controls Github organization (https://github.com/tango-controls/tango-conda-recipes) .
PyTango Conda recipes haven't been moved/copied yet.

### Tango meeting

Please register as soon as possible if you are planning on coming on this site: https://indico.esrf.fr/indico/event/41/

The site has all the info you need to organise your trip - thanks to the organisers Olga + Igor!

**Warning**: St Petersburg is a very popular destination especially with the White Nights festival and Euro 2020 football 
matches this year. You need to book flights + hotels soon if you want to get a seat!

### Tango documentation

Andy mentioned that some efforts should be done on improving the Tango event system documentation.
The [event system current documentation page](https://tango-controls.readthedocs.io/en/latest/administration/services/events.html) 
is currently only giving details about the multicast protocol which does not seem to be used by anyone.

**Action - S2Innovation?**: Create an issue in tango-doc (if does not exist yet) to ask for an improvement of the event 
system documentation.

### HDB++

A new issue has been reported by Graziano in libhdbpp-mysql: Lost connection to MySQL server during query" issue [#10](https://github.com/tango-controls-hdbpp/libhdbpp-mysql/issues/10)

ESRF has implemented a service to remove data from HDB++ TimescaleDB for attributes configured with a TTL.

ESRF is currently working on implementing a decimation service when using TimescaleDB, starting with scalar attributes.

A new [hdbpp-timescale-project](https://github.com/tango-controls-hdbpp/hdbpp-timescale-project) repository has been created.
It gathers all the services and dependencies required to be able archive data using TimescaleDB.

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET (Paris time).

The next Tango kernel teleconf meeting will take place in 2 weeks on Thursday 12th March 2020 at 15:00 CET.

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2020/2020-02-13/Minutes.md#summary-of-remaining-actions)

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
use tango-controls. **Andy mentioned that his project seems to be dead now. 
It was a EU-funded project and seems to be no longer financed. We can remove this action.**

**Action - Soleil**: Implement the fix for events with network aliases. **Gwenaelle should be able to work on this 
during the week 9th-13th March**

**Action - S2Innovation?**: Create a page in tango-doc where each institute could list the operating systems where cppTango and PyTango are running in their institutes.
It could probably be interesting to list as well the java versions used for the JTango applications. 
**An issue has been created by Michal to keep track of this request in tango-doc. 
No progress is foressen on that topic before the next teleconf meeting** 

**Action - volunteers**: Review TangoSourceDistribution PRs.

**Action - ESRF**: Move conda recipes to a new repository in tango-controls Github organization. 
**Done. Repository is now available on github: https://github.com/tango-controls/tango-conda-recipes . 
PyTango recipes still need to be transferred** 

**Action - cppTango developers and volunteers**: Review the TangoTest PRs.

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

**Action - Soleil**: Implement the fix for events with network aliases.

**Action - S2Innovation?**: Create a page in tango-doc where each institute could list the operating systems where cppTango and PyTango are running in their institutes.
It could probably be interesting to list as well the java versions used for the JTango applications. 

**Action - volunteers**: Review TangoSourceDistribution PRs.

**Action - ESRF?**: Move pytango conda recipes to a new repository in tango-controls Github organization.

**Action - cppTango developers and volunteers**: Review the TangoTest PRs.

**Action - S2Innovation?**: Create an issue in tango-doc (if does not exist yet) to ask for an improvement of the event 
system documentation.
