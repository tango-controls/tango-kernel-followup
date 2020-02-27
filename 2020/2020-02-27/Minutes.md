# Tango Kernel Follow-up Meeting - 2020/02/27

Held on 2020/02/27 at 15:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants:  Reynald Bourtembourg (ESRF), 

# Minutes

## Tango Source Distribution

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


## PyTango News

## High priorities issues

## AOB

### Conda packages

Conda recipes have been moved to a new repository in tango-controls Github organization (https://github.com/tango-controls/tango-conda-recipes) .

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
use tango-controls.

**Action - Soleil**: Implement the fix for events with network aliases.

**Action - S2Innovation?**: Create a page in tango-doc where each institute could list the operating systems where cppTango and PyTango are running in their institutes.
It could probably be interesting to list as well the java versions used for the JTango applications.

**Action - volunteers**: Review TangoSourceDistribution PRs.

**Action - ESRF**: Move conda recipes to a new repository in tango-controls Github organization. 
**Done. Repository is now available on github: https://github.com/tango-controls/tango-conda-recipes** 

**Action - cppTango developers and volunteers**: Review the TangoTest PRs.
