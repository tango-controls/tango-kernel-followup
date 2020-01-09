# Tango Kernel Follow-up Meeting - 2020/01/09

Held on 2020/01/09 at 15:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants: Andrew Goetz, Reynald Bourtembourg (ESRF), ...

# Minutes

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2019-11-26/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would 
like to get solved first.

**Action - All**: Test [9.3.4-rc2](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc2) release.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the TangoSourceDistribution repository.

**Action - S2Innovation**: Piotr said he will take care of the documentation issues reported while preparing this 9.3.4 Tango source distribution release.
Piotr will also update the Tango documentation to add links to rpm files created/used by Max IV. 

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - JTango team**: Investigate openjdk7 install failure on Travis

**Action - ESRF**: Update JTango 9.5.18 release notes to better describe the problem which has been solved. **Done**

**Action - TangoSourceDistribution team**: Use this new JTango release in 9.3.4 source distribution release.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - S2Innovation**: Michal Liszcz will ping Zbigniew Reszela about the issue [pytango#292](https://github.com/tango-controls/pytango/pull/292) and see whether [pytango#315](https://github.com/tango-controls/pytango/pull/315) is due to a similar problem.

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could 
use tango-controls.

**Action - cppTango developers and volunteers**: Review [cppTango#551](https://github.com/tango-controls/cppTango/pull/551), 
[cppTango#555](https://github.com/tango-controls/cppTango/pull/555) and 
[cppTango#552](https://github.com/tango-controls/cppTango/pull/552) Pull Requests

**Action - Thomas Braun**: Ping Frédéric Picca to get an update on the status and to know whether some help from us is required.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - Thomas Braun**: Thomas will prepare a Pull Request documenting the contribution process and merging policy.

**Action - ESRF**: Contact Gwenaëlle to see whether Soleil could implement the fix for events with network aliases. 

**Action - Geoff**: Push the latest developments to [pytango pybind11 branch](https://github.com/tango-controls/pytango/tree/pybind11) on Github tango-controls pytango repository.

**Action - cppTango team**: coordinate on slack to decide who will work on [cppTango#511]((https://github.com/tango-controls/cppTango/issues/511)) issue.
**Michal has been working on it and is waiting for comments and review.**

**Action - S2Innovation**: S2Innovation will call for a technical meeting dedicated to these SKA docker images. 
The tango kernel developers, some SKA members and S2Innovation (at least) will be invited. **The meeting took place.**

**Action - ESRF**: Send a Doodle-like survey to decide on the best weekday and time for regular Tango Kernel meetings.**Done. Tango Kernel meetings will take place on 2nd and 4th Thursday of each month**

## Tango Source Distribution

- New release candidate?
- Tango Database DS crash [TangoSourceDistribution#61](https://github.com/tango-controls/TangoSourceDistribution/issues/61)


## cppTango News

Questions raised in [cppTango#648](https://github.com/tango-controls/cppTango/issues/648): Possibility to use boost libraries?

### Stalled Pull Requests

## JTango News

## PyTango News

## High priorities issues

## AOB

### Next teleconf meeting

Tango kernel teleconf meeting tak place on the 2nd and 4th Thursday of each month, at 15:00 CET (Paris time).

The next Tango kernel teleconf meeting will take place on Thursday 23rd January 2020 at 15:00 CET.

## Summary of remaining actions

