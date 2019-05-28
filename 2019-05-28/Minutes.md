# Tango Kernel Follow-up Meeting - 2019/05/28

Held on 2019/05/28 at 15:00 CEST on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants: Reynald Bourtembourg, Andrew Goetz (ESRF), Sergi Rubio (ALBA), 
              Piotr Goryl, Michal Liszcz (S2Innovation), Thomas Braun (byte physics),
              Ireneusz Zadworny (SOLARIS)

# Minutes

## Tango Source Distribution

9.3.3 release is being prepared in [TangoSourceDistribution#18](https://github.com/tango-controls/TangoSourceDistribution/pull/18).

Users can test it by using [prepare-9.3.3](https://github.com/tango-controls/TangoSourceDistribution/tree/prepare-9.3.3) branch.

Michal Liszcz proposed [TangoSourceDistribution#33](https://github.com/tango-controls/TangoSourceDistribution/pull/33) 
to provide a dummy liblog4tango library so the users could use directly their device servers which were compiled with an 
older tango 9 version, without having the need to recompile them.
 
Frédéric Picca was contacted via e-mail to get some feedback to know whether there is any issue when building official Debian Packages 
from the prepare-9.3.3 TangoSourceDistribution branch.

[TangoSourceDistribution#36](https://github.com/tango-controls/TangoSourceDistribution/pull/36) was created in order to 
give the possibility for Pogo to generate CMakeLists.txt files.

**Action - ESRF**: Test [TangoSourceDistribution#36](https://github.com/tango-controls/TangoSourceDistribution/pull/36) Pull Request on old compilers (gcc 4.4)
 
[TangoSourceDistribution#37](https://github.com/tango-controls/TangoSourceDistribution/pull/37) was created to update 
the different SW components provided by the Tango Source Distribution.
TangoSourceDistribution 9.3.3 will provide at least JTango 9.5.14.

Readme, install and release notes files still need to be updated before having an official release.

**Action - ESRF**: Reynald Bourtembourg will prepare a file listing the most important changes provided by this new version and 
explaining how to upgrade from a previous version. This will be presented during the Tango meeting too.

At least a release candidate version of the Tango Source Distribution will be tagged before or during the Tango meeting 
and will be advertised there. 

## Tango meeting in Hamburg

It looks like there is no presentation foreseen yet about pyTango during the next Tango meeting.
Sergi will contact the experts and see whether they can contribute some slides which could be presented during the Tango Meeting.
It would be good to get some slides about JTango too.

**Action - Alba**: Provide some slides giving the latest news from PyTango for the Tango meeting

**Action - JTango team**: Provide some slides giving the latest news from JTango for the Tango meeting

## cppTango News

Igor Khokhriakov worked on ([cppTango#551](https://github.com/tango-controls/cppTango/pull/551)) to implement the 
server_init_hook() feature. It needs to be reviewed and tested.

Michal Liszcz created [cppTango#555](https://github.com/tango-controls/cppTango/pull/555) to solve crash during alarm 
state evaluation if the attribute value is not set. He said there are several ways to fix the issue. 
This PR needs to be reviewed and a decision must be taken on way to implement the fix.

Reynald Bourtembourg created [cppTango#552](https://github.com/tango-controls/cppTango/pull/552) to fix bug which could lead 
to a crash when reading a forwarded state attribute. This PR needs to be reviewed too.
 
Thomas Braun wanted to highlight [cppTango#530](https://github.com/tango-controls/cppTango/pull/530) (CMake: Add compile 
check to test for correct ZeroMQ C++ headers). Comments and reviews are needed and welcome.
cppTango does not compile when using the master branch of cppzmq. So it will probably not compile with the next release of cppzmq.

Reynald said that the next Pull Request to be merged will be [cppTango#526](https://github.com/tango-controls/cppTango/pull/526) 
which was proposed by Michal and which should reduce the compilation time. 
He invited Thomas Braun to review this PR before we merge it.

**Action - cppTango developers and volunteers**: Review [cppTango#551](https://github.com/tango-controls/cppTango/pull/551), 
[cppTango#555](https://github.com/tango-controls/cppTango/pull/555), [cppTango#552](https://github.com/tango-controls/cppTango/pull/552), 
[cppTango#530](https://github.com/tango-controls/cppTango/pull/530) and 
[cppTango#526](https://github.com/tango-controls/cppTango/pull/526) Pull Requests

## JTango News

JTango 9.5.14 has just been released but is not synchronized with Maven Central.

Igor created [JTango#74](https://github.com/tango-controls/JTango/pull/74) and proposed a solution to fix this issue.
The Travis build failed on this PR when using Java7. Igor suggested to drop the support for Java7 if no one is still using it.
Gwenaëlle Abeille commented after the Tango kernel teleconf, saying that they still need java7 support because they use it 
inside their SCADA tool which does not support java8 yet.

JTango 9.5.14 fixes a bug related to event reconnection when the device server is running on a host having multiple network 
interfaces ([JTango#71](https://github.com/tango-controls/JTango/pull/71)).

## PyTango News

Some complaints have been made in [pytango#273](https://github.com/tango-controls/pytango/pull/273) about a change of behaviour 
in cppTango related to the change of behaviour of DeviceAttribute.is_empty.

**Action - Alba**: Give more details about the issue [pytango#273](https://github.com/tango-controls/pytango/pull/273). 
In any case, this can be discussed at the coming Tango meeting.

ESRF would like to get a fix to [pytango#268](https://github.com/tango-controls/pytango/issues/268) in the next release.

## Waltz News

**Action - All**: Users are encouraged to test latest Waltz version and to provide feedback.

## TangoBox News

The TangoBox has been updated to use a more recent version of the TangoSourceDistribution prepare-9.3.3 branch.
So it gets recent fixes and features from that branch. The Java logback issue is now fixed.

**Action - All**: Users are encouraged to test the new TangoBox and to provide feedback.

## High priorities issues

**Action - All**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would 
like to get solved first.

## AOB

### HDB++
HDB++ TimescaleDB C++ insertion and Java extraction libraries are being developed.
The insertion library will be tested against the HDB++ Event Subscribers in the coming days. 
The DB schema is not the same as the one used by the PostgreSQL HDB++ library.
TimescaleDB HDB++ C++ insertion library source code (including the new DB schema) will be published on Github before the 
Tango meeting. We can discuss it briefly during the Tango meeting.  

### Pogo
Pascal Verdier is currently trying to update POGO in order to use the latest version of xtend/xtext which was released in April 2019.

The good news is that xtend/xtext seems to be still actively maintained (Java11 is already supported). 
The bad news is that Pogo is currently using quite an old version of xtend/xtext and there is quite some work to be done 
to use this new version. But it should be possible to use it.

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2019-05-09/Minutes.md#summary-of-remaining-actions)

**Action - Any (Windows) C++ developer willing to help**: Please help us to solve the Windows specific issues. For 
instance, there is a compilation issue on Windows with cppTango #480 (https://github.com/tango-controls/cppTango/pull/480).

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would 
like to get solved first.

**Action - Anyone willing to help**: Igor is welcoming any additional advice/help anyone could have to help debugging 
the JTango random timeouts issue.

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could 
use tango-controls.

**Action - ESRF**: Flag cppTango 9.3.3 as stable release and advertise it. 
**cppTango 9.3.3 has been flaged as stable release. It will be advertise during the next Tango meeting next week.**

**Action - All**: Test cppTango 9.3.3 and provide feedback.

**Action - IK**: Work on server_init_hook() ([cppTango#498](https://github.com/tango-controls/cppTango/issues/498)). **To be reviewed/tested**

**Action - ESRF-IK**: Organize a teleconf with Igor to agree on the tasks to be done. **We will do that during the Tango meeting**

**Action - All**: Users are encouraged to test the [sys-tango-benchmark](https://github.com/tango-controls/sys-tango-benchmark) tools before the next Tango meeting at Hamburg (beginning of June) and to provide feedback.

**Action - S2Innovation**: Work on [TangoSourceDistribution#30](https://github.com/tango-controls/TangoSourceDistribution/issues/30). **Done.**

**Action - All**: Users are encouraged to test [prepare-9.3.3](https://github.com/tango-controls/TangoSourceDistribution/tree/prepare-9.3.3) TangoSourceDistribution branch and to provide feedback.

**Action - ESRF**: Create an Indico page with a draft agenda for ICALEPCS TANGO workshop. **Will be done before the Tango meeting**

**Action - ESRF**: Fix [JTango#71](https://github.com/tango-controls/JTango/issues/71). **Done**

**Action - All**: Users are encouraged to test latest Waltz version and to provide feedback.

**Action - ESRF, Elettra, Alba, other institutes interested in contributing to HDB++**: Decide how to organize the next HDB++ meeting. To be discussed during the next Tango meeting in Hamburg.

**Action - S2Innovation**: Add Java logback fix to TangoBox 9.3.3. **Done**

**Action - All**: Users are encouraged to test the new TangoBox and to provide feedback.

**Action - All**: Submit abstracts for the next Tango meeting in Hamburg: https://indico.desy.de/indico/event/22850/call-for-abstracts. Deadline is 15th May 2019. **Done**

**Action - Anyone willing to help**: There are difficulties to regenerate a POGO package. More details on [pogo#58](https://github.com/tango-controls/pogo/issues/58). **Problem solved**

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