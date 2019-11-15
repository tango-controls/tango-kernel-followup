# Tango Kernel Follow-up Meeting - 2019/11/15

Held on 2019/11/15 at 15:00 CEST on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants: Reynald Bourtembourg, Andrew Goetz (ESRF)

# Minutes

## Tango Source Distribution

[9.3.4-rc2](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc2) has been released.

**Action - All**: Test [9.3.4-rc2](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc2) release.

## cppTango News

A new branch 9.3-backports has been created to provide bug fixes and small improvements for the cppTango 9.3 compatible versions.

### Require newer C++ compilers

In the cppTango project we would like to move to C++11/C++14.
For this we would require newer minimum compiler versions.
It would be interesting to hear which old OS versions still need to be supported.
### Require newer cmake version. 
As we move to more C++11 features, it would avoid a lot of additional work if we could use a newer cmake
version which has the required checks builtin. 
From reading [[1]] it seems 3.7 would be good already, this was shipped with debian stretch (oldstable).
Older distros can just download/compile a newer cmake version version as we do now for debian wheezy [[2]]. 

### cppTango next release number
cppTango next release number (9.4 or 10.0?) [#593](https://github.com/tango-controls/cppTango/pull/593)

### Stalled Pull Requests

- Question raised in [#555](https://github.com/tango-controls/cppTango/pull/555) (Fix crash during alarm state evaluation if attribute value is not set)
- Questions raised in [#504](https://github.com/tango-controls/cppTango/pull/504) (PR to fix #368): Pushing events for State and Status with quality factor and timestamp.
- [#620](https://github.com/tango-controls/cppTango/issues/620), [#540](https://github.com/tango-controls/cppTango/issues/540) 
and [#592](https://github.com/tango-controls/cppTango/issues/592) follow-up?
- [#551](https://github.com/tango-controls/cppTango/pull/551)) to implement the 
server_init_hook() feature. Changes were requested by Thomas Braun.
- [#480](https://github.com/tango-controls/cppTango/pull/480): DevEnum Support for commands

Reynald Bourtembourg created [cppTango#552](https://github.com/tango-controls/cppTango/pull/552) to fix bug which could lead 
to a crash when reading a forwarded state attribute. This PR needs to be reviewed too.

## JTango News

An issue has been observed at the ESRF with some Java GUIs subscribing to a big number of events.
We observed that the first event subscription ZMQ message(s) could be dropped silently by jeromq (not sent on the network) 
when trying to subscribe to an attribute on a remote device server. This issue occurs after a big number of event subscriptions and 
when subscribing to an attribute of a remote device server which had not been contacted yet by jeromq for this GUI. 
A fix has been found by setting the SendHwm to 0 on the ZMQ sockets used on the subscriber side.
Here is the commit fixing this issue: https://github.com/tango-controls/JTango/commit/b00043a5df6bd6b4bd95e2ce35c92b871f2e99a7

Travis for openjdk 7 failed. This needs to be investigated.

## PyTango News

ESRF would like to get a fix to [pytango#268](https://github.com/tango-controls/pytango/issues/268) in the next release.

## High priorities issues

**Action - All**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would 
like to get solved first.

## AOB

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2019-05-28/Minutes.md#summary-of-remaining-actions)

## Summary of remaining actions

**Action - Any (Windows) C++ developer willing to help**: Please help us to solve the Windows specific issues. For 
instance, there is a compilation issue on Windows with cppTango #480 (https://github.com/tango-controls/cppTango/pull/480).

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would 
like to get solved first.

**Action - Anyone willing to help**: Igor is welcoming any additional advice/help anyone could have to help debugging 
the JTango random timeouts issue.

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could 
use tango-controls.

**Action - ESRF**: Advertise cppTango 9.3.3 as stable release. 

**Action - All**: Test cppTango 9.3.3 and provide feedback.

**Action - cppTango developers, Alba**: Review/Test PR on server_init_hook() ([cppTango#498](https://github.com/tango-controls/cppTango/issues/498))

**Action - All**: Users are encouraged to test the [sys-tango-benchmark](https://github.com/tango-controls/sys-tango-benchmark) tools before the next Tango meeting at Hamburg (beginning of June) and to provide feedback.

**Action - All**: Users are encouraged to test [prepare-9.3.3](https://github.com/tango-controls/TangoSourceDistribution/tree/prepare-9.3.3) TangoSourceDistribution branch and to provide feedback.

**Action - ESRF**: Create an Indico page with a draft agenda for ICALEPCS TANGO workshop. **Will be done before the Tango meeting**

**Action - All**: Users are encouraged to test latest Waltz version and to provide feedback.

**Action - ESRF, Elettra, Alba, other institutes interested in contributing to HDB++**: Decide how to organize the next HDB++ meeting. To be discussed during the next Tango meeting in Hamburg.

**Action - All**: Users are encouraged to test the new TangoBox and to provide feedback.

**Action - ESRF**: Test [TangoSourceDistribution#36](https://github.com/tango-controls/TangoSourceDistribution/pull/36) 
Pull Request on old compilers (gcc 4.4)

**Action - Alba**: Give more details about the issue [pytango#273](https://github.com/tango-controls/pytango/pull/273). 
In any case, this can be discussed at the coming Tango meeting.

**Action - ESRF**: Reynald Bourtembourg will prepare a file listing the most important changes provided by this new version and 
explaining how to upgrade from a previous version. This will be presented during the Tango meeting too.

**Action - Alba**: Provide some slides giving the latest news from PyTango for the Tango meeting

**Action - JTango team**: Provide some slides giving the latest news from JTango for the Tango meeting

**Action - cppTango developers and volunteers**: Review [cppTango#551](https://github.com/tango-controls/cppTango/pull/551), 
[cppTango#555](https://github.com/tango-controls/cppTango/pull/555), [cppTango#552](https://github.com/tango-controls/cppTango/pull/552), 
[cppTango#530](https://github.com/tango-controls/cppTango/pull/530) and 
[cppTango#526](https://github.com/tango-controls/cppTango/pull/526) Pull Requests

**Action - Alba**: Give more details about the issue [pytango#273](https://github.com/tango-controls/pytango/pull/273). 
In any case, this can be discussed at the coming Tango meeting.