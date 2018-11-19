# Tango Kernel Follow-up Meeting - 2018/11/15

Held on 2018/11/15 at 14:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants: Reynald Bourtembourg, Andrew Goetz (ESRF), Igor Khokhriakov (IK), Lorenzo Pivetta (SKAO),
              Sergi Rubio, Zbigniew Reszela (ALBA), Ireneusz Zadworny (SOLARIS)

Short visit: Gwenaelle Abeillé (SOLEIL), Jean-Michel Chaize, Pascal Verdier (ESRF)



# Minutes

## Introduction
Many sound problems (echo, issues with microphone...) occurred during this meeting. 
Some participants could not talk and could not understand very well the others. The news from Igor listed in these minutes were not said during the meeting due to these technical problems and are based on an e-mail sent by Igor after the meeting.

## Next Tango kernel and documentation meeting (where and when?)

Following the results of the poll, the next Tango kernel and documentation meeting will take place during the week #6 (week from 4th-8th February) in 2019.
The meeting will be hosted by Solaris in Krakow (Poland). Many Thanks to Solaris. 
The precise dates were not discussed during the teleconference.
After the teleconference, Andy was proposing to start the kernel and documentation meeting on Monday 4th February 2019 at the beginning of the afternoon and to end it on Thursday in the middle of the day to get 3 full days of meeting.
This will have to be confirmed asap so people can start organizing their trip. 

## cppTango News (cppTango 9.3.2, ...)
cppTango 9.3.2 has been installed on the ESRF accelerator control system in October during the shutdown.
A compatibility issue [cppTango#492](https://github.com/tango-controls/cppTango/issues/492) has been discovered during the accelerator restart phase. Due to the lack of time to fully debug the problem, the previous version (9.2.5) has been re-installed.
Tango 9.3.2 is still installed, but only on the Debian 9 hosts, so only for a small part of the ESRF accelerator control system.
A patch to solve [cppTango#492](https://github.com/tango-controls/cppTango/issues/492) is available in the description of the issue.

Reynald would like to create new tests in the cppTango test suite to test [cppTango#492](https://github.com/tango-controls/cppTango/issues/492) proposed patch.  

Some other issues have been discovered since the previous Tango kernel teleconf meeting:
- [cppTango#458](https://github.com/tango-controls/cppTango/issues/458) has been reopened: 
cppTango 9.3.0 and 9.3.1: Issue with dynamic attributes. There is still an issue when a device server is exporting several devices from the same class and these devices are creating different dynamic attributes. There can be a crash during a device restart. 
- [cppTango#496](https://github.com/tango-controls/cppTango/issues/496): 
Client subscribing to events can be blind for up to 200 seconds if the target device is restarted (device restart)
- [cppTango#495](https://github.com/tango-controls/cppTango/issues/495):
Incorrect getting of the list of devices from a pattern for Tango::Group if using a remote host.

The plan is that cppTango 9.3.3 will not be released before [cppTango#492](https://github.com/tango-controls/cppTango/issues/492) and [cppTango#458](https://github.com/tango-controls/cppTango/issues/458) are fixed.

Igor has still about 80 hours which can be spent on cppTango.

## Windows support (VS2017support, ...)

ESRF received some answers from Elettra, Soleil, Thales listing the Microsoft compilers they need support for.
Here is the list of compilers versions on Windows for which support has been requested:

- MSVC9 - 32 bits (Thales)
- MSVC12 - 32 bits (Soleil, Thales)
- Visual Studio 2017 - 64 bits (ESRF)

Elettra is currently compiling for Windows 7 32 bits with Microsoft Visual C++ 2010 Express SP1 (Elettra) but is progressively switching to Windows 10 64 bits with Microsoft Visual C++ 2010 Express SP1 or more recent (Elettra)

Please update the following forum section if you need support for other compiler versions on Windows: http://www.tango-controls.org/community/forum/c/general/rfc/old-windows-compilers-support

**Action - Solaris**: Send a link to ESRF to the cppTango Visual Studio 2017 artifacts. **Done immediately after the meeting**. Thanks Irek!

## Tango Source Distribution

Igor worked on this topic and created a Pull Request [TangoDistribution#8](https://github.com/tango-controls/TangoSourceDistribution/pull/8) which is ready for merging. If some institutes could give it a try and provide feedback, that would be great.
 Igor tested it on Debian Jessie & Stretch everything compiles and runs smoothly. If ALBA could do more tests, this would be perfect!

**Action - Alba, All institutes**: Review [TangoDistribution#8](https://github.com/tango-controls/TangoSourceDistribution/pull/8)

## JTango News

- Igor backported multiple sockets binding for Events in JTango, should be fine to merge.

Igor: "I think the issue that Reynald mentioned during the previous meeting is a different one... I guess that's the one when one launches Jive and sees "Host not found" error message. To fix this we need to backport another fix from master. I could try to do so, but as far as I remember that one breaks API."

**Action - ESRF, IK**: JTango: clarify actions to be done to fix the event reconnection issues with java clients subscribing to events coming from hosts having several network intefaces"

- Igor forked JTango and will maintain it further independently from JTango.

## PyTango News

Vincent Michel will leave the ESRF mid-December and will no longer work on PyTango after this date.

## Waltz News

- rc5&rc6 on their way. Igor hopes to finish it this week (#46). So starting from next week he can put more efforts into
 cppTango

- Tango WebUI workshop at Lund was fine. SKA will evaluate Waltz as their base solution for GUIs, if so they promised 
man power. 

## TangoBox status

s2Innovation is preparing a new Tango Box based on the latest Ubuntu LTS release.

## Go through main issues and define priorities

Zibi mentioned [TangoTickets#7](https://github.com/tango-controls/TangoTickets/issues/7).

**Action - ESRF**: Add [TangoTickets#7](https://github.com/tango-controls/TangoTickets/issues/7) issue to the list of 
issues to be handled in tango 9 LTS github project. 
**[cppTango#498](https://github.com/tango-controls/cppTango/issues/498) has been created just after the teleconf and 
added to Tango 9 LTS github project**.

## AOB

### HDB++
ESRF is evaluating TimescaleDB is a potential replacement for Cassandra. The first tests are very promising.

Alba developed a Polling archiver for HDB++ to workaround the issues with the events and their firewalls.

Alba developed an archiver which is able subscribe to change events instead of archive events if the archive events are 
not configured for the attribute. This was developed to be able to archive Tango 7 attributes where performances are 
required.

**Action**: Organize an HDB++ meeting in 2019. Maybe dedicate a full day for an HDB++ meeting during the week of the 
next Tango meeting at DESY.

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2018-09-14/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Every institute will send the Windows compiler versions they need (if needed) to Reynald. 
**Done for many institutes** (See Windows support section of these minutes).

**Action - Any (Windows) C++ developer willing to help**: Please help us to solve the Windows specific issues. 
For instance, there is a compilation issue on Windows with cppTango #480 (https://github.com/tango-controls/cppTango/pull/480).

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would 
like to get solved first.

**Action - Igor**: Igor volunteered to spend some hours from his contract on the Tango Source Distribution. 
**Work done in [TangoDistribution#8](https://github.com/tango-controls/TangoSourceDistribution/pull/8)** 

**Action - ESRF**: ESRF will create something like a Doodle to find the best dates for the next Tango kernel and 
documentation meeting. **Done**

**Action - Igor?**: A PR with the backport of JTango fix for the reconnection bug when there are several network 
interfaces will have to be created especially for tango-9-lts, adapting the original PR to avoid all the deprecations 
it introduced originally. **[JTango#60](https://github.com/tango-controls/JTango/pull/60) has been created**

**Action - Anyone willing to help**: Igor is welcoming any additional advice/help anyone could have to help debugging 
the JTango random timeouts issue.

**Action - Igor**: Igor will contact JetBrains to renew the JetBrains licenses used by the Tango kernel developers. 
**Done - Licences renewed! Many thanks Igor and JetBrains**

**Action - S2Innovation**: Prepare a new version of the TangoBox where the Tango events are working properly. **WIP**

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could 
use tango-controls. **To be done**

## Summary of remaining actions

**Action - All institutes**: Every institute will send the Windows compiler versions they need (if needed) to Reynald.

**Action - Any (Windows) C++ developer willing to help**: Please help us to solve the Windows specific issues. For 
instance, there is a compilation issue on Windows with cppTango #480 (https://github.com/tango-controls/cppTango/pull/480).

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would 
like to get solved first.

**Action - Anyone willing to help**: Igor is welcoming any additional advice/help anyone could have to help debugging 
the JTango random timeouts issue.

**Action - S2Innovation**: Prepare a new version of the TangoBox where the Tango events are working properly. **WIP**

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could 
use tango-controls. **To be done**

**Action - Alba, All institutes**: 
Review [TangoDistribution#8](https://github.com/tango-controls/TangoSourceDistribution/pull/8)

**Action**: Organize an HDB++ meeting in 2019. Maybe dedicate a full day for an HDB++ meeting during the week of the 
next Tango meeting at DESY.

**Action - ESRF, IK**: JTango: clarify actions to be done to fix the event reconnection issues with java clients 
subscribing to events coming from hosts having several network intefaces"
