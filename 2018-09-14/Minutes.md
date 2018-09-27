# Tango Kernel Follow-up Meeting - 2018/09/14

Held on 2018/09/14 at 14:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants: Reynald Bourtembourg, Andrew Goetz (ESRF), Igor Khokhriakov (HZG-IK), Lorenzo Pivetta (SKA-O), Geoffrey Mant (STFC), Jairo Moldes (ALBA), Claudio Scafuri (ELETTRA)



# Minutes
## 1. cppTango News (cppTango 9.3.2rc, SonarQube, coverall, backports from Tango 10 development branch, ...)
cppTango 9.3.2 has been (pre-)released this week. It is installed on parts of the ESRF control system since Tuesday 11th September 2018. No problem reported so far. Please test this version if you can.
It mainly solve some issues related to events. In theory, device servers compiled with an older Tango 9 version do not need to be recompiled to work with this new version but there could be some pitfalls due to the fact that libtango and liblog4tango libraries have been merged together in libtango.
It is no longer required to link with liblog4tango so some files used by POGO should be updated to avoid this unecessary link.

Igor integrated SonarQube and Coverall in cppTango. This gives very nice reports on Test Coverage status and code analysis.

He also worked on backporting some other PR from Tango 10 development branch into tango-9-lts.

Igor spent some time to analyze the existing code. He created a document explaining the current code design and suggesting improvements and he also created the following PRs to improve the polling system and the event system:
- https://github.com/tango-controls/cppTango/pull/470
- https://github.com/tango-controls/cppTango/pull/472

Links to the design document are provided in these PRs which can be used as entry points for discussions to improve the current design.

## 2. Windows support (VS2017support, appveyor artefacts retention policy, Solaris contribution...)

appveyor builds have been repaired thanks to the work done by Sébastien Gara and Reynald Bourtembourg.

We will need to agree on a limited list of MSVC compilers to put in the automatic builds to avoid to slow them down too much.
It is possible to build for all the old compilers and new compilers after every commit/PR, using APPVEYOR_BUILD_WORKER_IMAGE tweak variable as described in appveyor documentation (https://www.appveyor.com/docs/build-environment/#using-multiple-images-for-the-same-build) but we should still limit the number of compilers used for each build to speed up the builds.
We agreed to wait for the next Tango kernel teleconf meeting to get more feedback from the users before to update the list of msvc compilers used by appveyor at each build.
If the list is too big, it will be restricted to a few compilers and the artifacts for the other needed compilers will be built from another branch just before creating new cppTango releases.

**Action - All institutes**: Every institute will send the Windows compiler versions they need (if needed) to Reynald.

Igor expressed his worries about maintaining cppTango for Windows because it is difficult for him to test it on Windows and we don't get much help from the community when there is a compilation issue on a Windows compiler.

**Action - Any (Windows) C++ developer willing to help**: Please help us to solve the Windows specific issues. For instance, there is a compilation issue on Windows with cppTango #480 (https://github.com/tango-controls/cppTango/pull/480).

## 3. Tango Source Distribution (Solaris contribution)

The Solaris team is extremely busy at the moment and they don't know yet until when so they couldn't and cannot work on this topic for the moment.

**Action - Igor**: Igor volunteered to spend some hours from his contract on the Tango Source Distribution.

**Ingvord**: the progress can be tracked in [this PR](https://github.com/tango-controls/TangoSourceDistribution/pull/8). Shortly speaking some additional work is required in some Tango components before we can start to assemble new distributions. Namely, add CMake files to some C++ projects (make environment independent existing ones); ensure proper maven releases (especially of pogo) etc.

## 4. Next Tango kernel and documentation meeting (where and when?)

It appears that several institutes will be very busy until the end of this year so this Tango kernel and documentation meeting (3 days meeting) will not take place in 2018.
Solaris would still be happy to host this meeting at Krakow at the beginning of next year.

**Action - ESRF**: ESRF will create something like a Doodle to find the best dates for this meeting.

## 5. Go through the main issues and define priorities

Andy mentioned the issue reported by Matej Komel from Coyslab (cppTango #482).
Reynald said this issue is not a high priority issue because this is happening only the first time the device server is started.
Moreover, there might be a workaround if this is problematic, writing _polled_attr_ system property before starting the device server the first time might solve the issue.

According to Reynald, the most critical issues to be solved in cppTango are cppTango #368 (Pushing events with a value for state and status triggers a memory leak) and cpptango #359 (Change event subscription blind to change events right after device server restart).

Users are invited to vote for the issues which are the most critical for them by commenting "+1" on the github issues. They can also use the thumb-up on the description of the issue but this has the (dis)advantage to avoid to generate e-mails on the cppTango repository subscribers.

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would like to get solved.

There is a bug in JTango where an event client reconnection does not work properly when it is subscribing to events coming from a device server running on a host having several network interfaces, and when the first listed interface is the private network interface.
According to Igor, this bug is fixed in JTango master branch by binding to every network interface. Lorenzo mentioned that this could be a problem in some situations. Igor suggested to implement this simple solution first and to improve it with configuration options later. A PR with the backport of this fix will have to be created especially for tango-9-lts, adapting the original PR to avoid all the deprecations it introduced originally.

**Action - Igor?**: A PR with the backport of JTango fix for the reconnection bug when there are several network interfaces will have to be created especially for tango-9-lts, adapting the original PR to avoid all the deprecations it introduced originally.

**Ingvord**: See [JTango-60](https://github.com/tango-controls/JTango/pull/60)

Igor is facing a bug when using JTango. He gets some random timeouts from time to time when running on a highly loaded system.
He had a look at JacORB synchronization but the problem does not seem to come from there nor from the java garbage collector.
Andy suggested to decrease the timeout (from 3 seconds to few tens or hundreds of ms) to potentially increase the probablility of triggering the problem.
He also suggested to use wireshark to see what's happening on the network. Igor is welcoming any additional advice/help anyone could have to help debugging this issue.

**Action - Anyone willing to help**: Igor is welcoming any additional advice/help anyone could have to help debugging the JTango random timeouts issue.

**Ingvord**: looks like there similar issues already exist since ages: [JTango-18](https://github.com/tango-controls/JTango/issues/18) and [JTango-19](https://github.com/tango-controls/JTango/issues/19)

## 6. Waltz new release, deployment at ESRF

Waltz 0.6 has been released. Igor asked for some news about Waltz deployment at the ESRF.
For the moment, noone could work on this topic and noone has been assigned yet.

Lorenzo mentioned a meeting dedicated to web applications which will be organized at MaxIV around October. Some people from SKA will be present, as well as Igor.

## 7. JetBrains OS license renewal

**Action - Igor**: Igor will contact JetBrains to renew the JetBrains licenses used by the Tango kernel developers.

**Ingvord**: new licenses have been acquired

## 8. TangoBox status

Tango events do not work properly on the latest TangoBox (9.2_RC11). Piotr is preparing a new version based on Ubuntu 18.04 and will ensure the events work properly on the new one.

**Action - S2Innovation**: Prepare a new version of the TangoBox where the Tango events are working properly.

## 9. AOB (JTango?, PyTango?, ...?)

Geoff mentioned that he could work a bit on PyTango and will focus on having the test suite running as expected. He will spend some time at the ESRF at the end of September.

Andy mentioned a meeting between SKA and JYSE to try to find a way to get their code open sourced. He also mentioned that their new version is now able to talk directly on the Tango Bus without passing via the REST API (option).

A discussion about HDB++ DB backends occurred. SKA-ZA has some experience with timescaleDB. Andy will contact them to get more information. He will put Lorenzo in CC.

Lorenzo mentioned KX as another potential alternative investigated at some point by SKA but he also pointed out that this DB is not cheap at all and not open source.

It seems there were a bit less disconnection problems with this new videoconf system so we will continue to use VidyoConnect at the next meeting.

## 10. Status of Actions defined in the previous meetings:

The following tasks had been defined during the previous meetings:

**Action - ESRF**: ESRF will send an e-mail to tango-controls info mailing list and post a message on the forum to try to get some feedback from the users to know whether the old compilers support is still required.

The e-mail was sent and a new topic was posted on the forum. We got some feedback from users who need support for msvc9 and win32-msvc12.

**Action - ALBA** from previous teleconf meeting: ALBA will create a ticket in TangoTicket to request the possibility to specify the ports used by ZMQ.

Jairo wrote(!) that Sergi Rubio is the person to contact to get more information about this point.

**Action - Solaris**: Solaris will create a Doodle (or similar) to define place and/or dates.

This action is now the responsibility of the ESRF.

**Action - ESRF** : ESRF will create a repository (organization?) to host tango related tools which might be interesting for the community. ESRF will then inform the community.

The following github organization has been created for this purpose: https://github.com/tango-controls-tools and an e-mail has been sent to tango-controls info mailing list.

Please send an e-mail to Reynald to be invited to join this organization and get the permission to create and admin new repositories on this Github organization.

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could use tango-controls.

We keep this action because Andy could not do it before this meeting.

## Summary of remaining actions

**Action - All institutes**: Every institute will send the Windows compiler versions they need (if needed) to Reynald.

**Action - Any (Windows) C++ developer willing to help**: Please help us to solve the Windows specific issues. For instance, there is a compilation issue on Windows with cppTango #480 (https://github.com/tango-controls/cppTango/pull/480).

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would like to get solved first.

**Action - Igor**: Igor volunteered to spend some hours from his contract on the Tango Source Distribution.

**Action - ESRF**: ESRF will create something like a Doodle to find the best dates for the next Tango kernel and documentation meeting.

**Action - Igor?**: A PR with the backport of JTango fix for the reconnection bug when there are several network interfaces will have to be created especially for tango-9-lts, adapting the original PR to avoid all the deprecations it introduced originally.

**Action - Anyone willing to help**: Igor is welcoming any additional advice/help anyone could have to help debugging the JTango random timeouts issue.

**Action - Igor**: Igor will contact JetBrains to renew the JetBrains licenses used by the Tango kernel developers.

**Action - S2Innovation**: Prepare a new version of the TangoBox where the Tango events are working properly.

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could use tango-controls.
