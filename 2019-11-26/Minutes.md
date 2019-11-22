# Tango Kernel Follow-up Meeting - 2019/11/26

Held on 2019/11/26 at 13:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants: 

# Minutes

## Tango Source Distribution

## cppTango News

### Stalled Pull Requests

- Questions raised in [#504](https://github.com/tango-controls/cppTango/pull/504) (PR to fix #368): Pushing events for State and Status with quality factor and timestamp.
- [#551](https://github.com/tango-controls/cppTango/pull/551)) to implement the server_init_hook() feature. Changes were requested during Thomas Braun's review.
- [#480](https://github.com/tango-controls/cppTango/pull/480): DevEnum Support for commands

Reynald Bourtembourg created [cppTango#552](https://github.com/tango-controls/cppTango/pull/552) to fix a bug which could lead 
to a crash when reading a forwarded state attribute. This PR needs to be reviewed too.

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

## JTango News

## PyTango News

## High priorities issues

**Action - All**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would 
like to get solved first.

## AOB

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2019-11-15/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would 
like to get solved first.

**Action - All**: Test [9.3.4-rc2](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc2) release.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the TangoSourceDistribution repository.

**Action - S2Innovation**: Piotr said he will take care of the documentation issues reported while preparing this 9.3.4 Tango source distribution release.
Piotr will also update the Tango documentation to add links to rpm files created/used by Max IV. 

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - JTango team**: Investigate openjdk7 install failure on Travis

**Action - JTango team**: Release a new version of JTango and describe better the problem which has been solved, in the release notes.

**Action - TangoSourceDistribution team**: Use this new JTango release in 9.3.4 source distribution release.

**Action - All**: Please provide your availability in this [Framadate](https://framadate.org/JNHcEkDDOWl5lgOF) to help decide on the next meeting date and time.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - S2Innovation**: Michal Liszcz will ping Zbigniew Reszela about the issue [pytango#292](https://github.com/tango-controls/pytango/pull/292) and see whether [pytango#315](https://github.com/tango-controls/pytango/pull/315) is due to a similar problem.

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could 
use tango-controls.

**Action - cppTango developers and volunteers**: Review [cppTango#551](https://github.com/tango-controls/cppTango/pull/551), 
[cppTango#555](https://github.com/tango-controls/cppTango/pull/555) and 
[cppTango#552](https://github.com/tango-controls/cppTango/pull/552) Pull Requests

## Summary of remaining actions

