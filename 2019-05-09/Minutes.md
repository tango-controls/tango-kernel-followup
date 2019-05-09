# Tango Kernel Follow-up Meeting - 2019/05/09

Held on 2019/05/09 at 14:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants: Reynald Bourtembourg, Jean-Michel Chaize, Andrew Goetz (ESRF), Igor Khokhriakov (IK),
              Graziano Scalamera, Claudio Scafuri (Elettra), Jairo Moldes, Zbigniew Reszela (ALBA),
              Piotr Goryl, Michal Liszcz (S2Innovation)


# Minutes

## cppTango News

cppTango 9.3.3 has been installed on the ESRF accelerator simulators control systems and on the control system being built for the new accelerator.

No big issue reported so far.

Elettra tested it and improvements were noticed compared to the previous version.

cppTango 9.3.3 is also used in the latest TangoBox. No problem detected when using 9.3.3 clients and servers.
Some problems were noticed when mixing 9.2.5 and 9.3.3. Reynald mentioned that this might be expected in some specific cases because the resolution of the event problems involved a fix on both client and server side.

**Action - ESRF**: Flag cppTango 9.3.3 as stable release and advertise it.

**Action - All**: Test cppTango 9.3.3 and provide feedback.

Some support contracts have been agreed with S2Innovation and BytePhysics (Thomas Braun) to provide some support on cppTango and Tango Source Distribution.

The administrative part will be completed soon. Piotr Goryl and Michal Liszcz from S2Innovation will come to the ESRF next week for a couple of days. They will leave with some homework.

Igor mentioned that he still has ~40 hours to be spent on cppTango. 

**Action - IK**: Work on server_init_hook() ([cppTango#498](https://github.com/tango-controls/cppTango/issues/498))

**Action - ESRF-IK**: Organize a teleconf with Igor to agree on the tasks to be done.

## sys-tango-benchmark

Piotr presented the new Tango Benchmark tools in a few words.

They are available on the following Github repository: https://github.com/tango-controls/sys-tango-benchmark.

**Action - All**: Users are encouraged to test the [sys-tango-benchmark](https://github.com/tango-controls/sys-tango-benchmark) tools before the next Tango meeting at Hamburg (beginning of June) and to provide feedback.

## Tango Source Distribution

9.3.3 release is being prepared in [TangoSourceDistribution#18](https://github.com/tango-controls/TangoSourceDistribution/pull/18).

Users can test it by using [prepare-9.3.3](https://github.com/tango-controls/TangoSourceDistribution/tree/prepare-9.3.3) branch.

Michal Liszcz has fixed [TangoSourceDistribution#21](https://github.com/tango-controls/TangoSourceDistribution/issues/21).
 He will work on [TangoSourceDistribution#30](https://github.com/tango-controls/TangoSourceDistribution/issues/30) and will try to update 
the automake files to merge liblog4tango and libtango libraries.
The next release will be available after this has been fixed (if it's not too long and too difficult to fix).

Some cleanup needs to be done in the README, INSTALL, TANGO_CHANGES and similar files.

**Action - S2Innovation**: Work on [TangoSourceDistribution#30](https://github.com/tango-controls/TangoSourceDistribution/issues/30)

**Action - All**: Users are encouraged to test [prepare-9.3.3](https://github.com/tango-controls/TangoSourceDistribution/tree/prepare-9.3.3) TangoSourceDistribution branch and to provide feedback.

## ICALEPCS TANGO Workshop

A TANGO workshop will be organized again at the next ICALEPCS in October in New York. 
We are looking for volunteers and ideas of contributions.

Piotr, Andy and Reynald mentioned they are volunteers.

**Action - ESRF**: Create an Indico page with a draft agenda for ICALEPCS TANGO workshop.

## JTango News

There is still an event reconnection issue on java client side in a specific case: [JTango#71](https://github.com/tango-controls/JTango/issues/71).
Pascal Verdier will look at it. We basically need to do what was done on the latest cppTango version on the Java side.

Igor is using his JTango fork. No big issue so far for the way he is using it.

**Action - ESRF**: Fix [JTango#71](https://github.com/tango-controls/JTango/issues/71)

## PyTango News

Tiago Coutinho is now back at ALBA.

Some work is ongoing in trying to do some automatic builds for Windows.

Jairo Moldes mentioned some problems with appveyor which is deleting some files.

Reynald mentioned that this should be fixed by using links to files which have been added by Sébastien Gara to the [boost-ci github release page](https://github.com/tango-controls/boost-ci/releases).
These files links should be used instead of links to the appveyor artifacts (which are automatically deleted after 6 months).

## Waltz News

New releases with improvements concerning event notifications.
More details in the release notes of the following new versions:

* Release [v0.7](https://github.com/tango-controls/waltz/releases/tag/v0.7)
* Release [v0.7.1](https://github.com/tango-controls/waltz/releases/tag/v0.7.1)
* Release [v0.7.2](https://github.com/tango-controls/waltz/releases/tag/v0.7.2)

Igor will present these new versions during a talk at the next tango meeting.

**Action - All**: Users are encouraged to test latest Waltz version and to provide feedback.

## HDB++

Do we organize an HDB++ meeting this year? When and where?
Or do we go for some more regular teleconf meetings?

**Action - ESRF, Elettra, Alba, other institutes interested in contributing to HDB++**: Decide how to organize the next HDB++ meeting. To be discussed during the next Tango meeting in Hamburg.

Alba, Elettra and ESRF will work together on building and testing HDB++ benchmark tools in order to test the limits of HDB++ with the different supported backends.
The results will be published in a paper on HDB++ at ICALEPCS. 

## TangoBox status

TangoBox v9.3.3 has been released this morning (9th May 2019).
It has been prepared using [prepare-9.3.3](https://github.com/tango-controls/TangoSourceDistribution/tree/prepare-9.3.3) TangoSourceDistribution branch.

It is currently using a version of prepare-9.3.3 branch which is without the fix on Java logback file.
This fix will be added soon to the TangoBox.

**Action - S2Innovation**: Add Java logback fix to TangoBox 9.3.3

The TangoBox is using many docker containers. These containers have been updated in order to use the latest tango version.

The size of the TangoBox has been reduced compared to the previous version.

**Action - All**: Users are encouraged to test the new TangoBox and to provide feedback.

## Go through main issues and define priorities

**Action - All**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would 
like to get solved first.

## AOB

**Action - All**: Submit abstracts for the next Tango meeting in Hamburg: https://indico.desy.de/indico/event/22850/call-for-abstracts

Reynald forgot to mention the following during the teleconf but the readers of these minutes might be able to help:

**Action - Anyone willing to help**: There are difficulties to regenerate a POGO package. More details on [pogo#58](https://github.com/tango-controls/pogo/issues/58).

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2018-11-15/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Every institute will send the Windows compiler versions they need (if needed) to Reynald.
**Done**

**Action - Any (Windows) C++ developer willing to help**: Please help us to solve the Windows specific issues. For 
instance, there is a compilation issue on Windows with cppTango #480 (https://github.com/tango-controls/cppTango/pull/480).

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would 
like to get solved first.

**Action - Anyone willing to help**: Igor is welcoming any additional advice/help anyone could have to help debugging 
the JTango random timeouts issue. **Igor is currently using a work-around (retry) but fix would be welcome.**

**Action - S2Innovation**: Prepare a new version of the TangoBox where the Tango events are working properly. **Done**

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could 
use tango-controls. **To be done**

**Action - Alba, All institutes**: 
Review [TangoDistribution#8](https://github.com/tango-controls/TangoSourceDistribution/pull/8). **Done but new action to test prepare-9.3.3 branch**.

**Action**: Organize an HDB++ meeting in 2019. Maybe dedicate a full day for an HDB++ meeting during the week of the 
next Tango meeting at DESY. **Discussion will take place during the next Tango meeting to decide on the next HDB++ meeting**

**Action - ESRF, IK**: JTango: clarify actions to be done to fix the event reconnection issues with java clients 
subscribing to events coming from hosts having several network interfaces. **Done** 

## Summary of remaining actions

**Action - Any (Windows) C++ developer willing to help**: Please help us to solve the Windows specific issues. For 
instance, there is a compilation issue on Windows with cppTango #480 (https://github.com/tango-controls/cppTango/pull/480).

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would 
like to get solved first.

**Action - Anyone willing to help**: Igor is welcoming any additional advice/help anyone could have to help debugging 
the JTango random timeouts issue.

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could 
use tango-controls.

**Action - ESRF**: Flag cppTango 9.3.3 as stable release and advertise it.

**Action - All**: Test cppTango 9.3.3 and provide feedback.

**Action - IK**: Work on server_init_hook() ([cppTango#498](https://github.com/tango-controls/cppTango/issues/498))

**Action - ESRF-IK**: Organize a teleconf with Igor to agree on the tasks to be done.

**Action - All**: Users are encouraged to test the [sys-tango-benchmark](https://github.com/tango-controls/sys-tango-benchmark) tools before the next Tango meeting at Hamburg (beginning of June) and to provide feedback.

**Action - S2Innovation**: Work on [TangoSourceDistribution#30](https://github.com/tango-controls/TangoSourceDistribution/issues/30)

**Action - All**: Users are encouraged to test [prepare-9.3.3](https://github.com/tango-controls/TangoSourceDistribution/tree/prepare-9.3.3) TangoSourceDistribution branch and to provide feedback.

**Action - ESRF**: Create an Indico page with a draft agenda for ICALEPCS TANGO workshop.

**Action - ESRF**: Fix [JTango#71](https://github.com/tango-controls/JTango/issues/71)

**Action - All**: Users are encouraged to test latest Waltz version and to provide feedback.

**Action - ESRF, Elettra, Alba, other institutes interested in contributing to HDB++**: Decide how to organize the next HDB++ meeting. To be discussed during the next Tango meeting in Hamburg.

**Action - S2Innovation**: Add Java logback fix to TangoBox 9.3.3

**Action - All**: Users are encouraged to test the new TangoBox and to provide feedback.

**Action - All**: Submit abstracts for the next Tango meeting in Hamburg: https://indico.desy.de/indico/event/22850/call-for-abstracts. Deadline is 15th May 2019.

**Action - Anyone willing to help**: There are difficulties to regenerate a POGO package. More details on [pogo#58](https://github.com/tango-controls/pogo/issues/58).
