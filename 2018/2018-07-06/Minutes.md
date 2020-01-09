# Tango Kernel Follow-up Meeting - 2018/07/06

Held on 2018/07/06 at 10:00 CET on https://appear.in/tango-kernel

Participants: Reynald Bourtembourg, Andrew Goetz (ESRF), Claudio Scafuri (Elettra),
              Sergi Blanch-Torné (ALBA), Igor Khokhriakov (Ingvord), Geoffrey Mant (STFC),
              the whole(?) Solaris Team!

# Minutes
## 1. Windows support (VS2017 support, appveyor artifacts retention policy, Solaris contribution...)

With appveyor, it seems to be impossible to build for Visual Studio 2017 and at the same time to build with old Windows compilers (MSVC9, MSV10, MSVC12) on the same branch. 

It is suggested to build for Visual Studio 2017 and 2015 32 bits and 64 bits on tango-9-lts and to create a dedicated branch for the older compilers if they are still needed.

**Action - ESRF**: ESRF will send an e-mail to tango-controls info mailing list and post a message on the forum to try to get some feedback from the users to know whether the old compilers support is still required.

Appveyor artifacts retention policy specifies that the artefacts built automatically with appveyor are kept for 6 months maximum.

Therefore, we need to find a better way to distribute the generated Windows msi files.

Appveyor release build artifacts should be uploaded to GitHub release page. For this, current appveyor script must be altered. This work could be done by Sebastien Gara when he will restart to work on this topic.

omniorb and zmq repositories currently under Sebastien Gara's acount should be moved to tango-controls and we should ensure the Windows builds are not using artefacts which could expire after 6 months.

## 2. Tango Source Distribution (Solaris contribution)

Solaris will work on the resurrection of the Tango Source Distribution.

Ireneusz will work on this task in August.

Ingvord suggested to work on the following PR so others can easily follow the current status: 
PR for TangoSourceDistribution: [link](https://github.com/tango-controls/TangoSourceDistribution/pull/8)

Personal note from Reynald (thoughts after the meeting): I think this PR is useful because it lists all the tasks which need to be done to achieve the ultimate goal but I think we should avoid to have a monster PR which will be imposible to review... I rather encourage creating many small PRs easier to review.
If we don't want to commit unfinished work in the master branch, we could create a dedicated development branch and merge some PRs there. TangoSourceDistribution#8 could be altered as issue where we could track the progress of the different tasks. We could also use the GitHub project feature to follow up easily the progress of the different tasks.

## 3. cppTango News

Ingvord said that he will try to fix event system bugs in August + backport some V10 developments.

Reynald created a Docker image able to run a notifd (32 bits) and another one to run a Tango 7 TangoTest version.

Some new tests will be added to test basic backwards-compatibility with Tango 7 and Tango 8 device servers.

## 4. Go through the main issues and define priorities

Hihghest priority for ESRF is the event system and its backward compatibility. The dead line is the next shutdown in the winter 2018/19 but of course, the earlier, the better because it will allow the ESRF to test the new pre-release with a working accelerator control system asap.

## 5. AOB (JTango?, PyTango?, ...?)

JTango: An issue has been reported on the forum related to jive and recent java versions.
There was already a similar issue created on JTango Github repository: [Jtango issue #53](https://github.com/tango-controls/JTango/issues/53).
The easiest work-around is to use java 8. Another one has been suggested by Andy and Reynald:
http://www.tango-controls.org/community/forum/c/general/installation/installing-jive-on-debian-stretch/?page=2#post-3463

**Action - ALBA** from previous teleconf meeting: ALBA will create a ticket in TangoTicket to request the possibility to specify the ports used by ZMQ.

## 6. Other

Tango Kernel camp: Date must be specified, a suitable option (not for Reynald) is for a few days in between late September - early October; places: SOLARIS; DESY; ESRF; ???
Sergi suggested to work in subgroups during the code camp.

Ingvord suggested to create a doodle poll to define place and/or dates.

**Action - Solaris**: Solaris will create a Doodle (or similar) to define place and/or dates.

Andy highlighted a PR from SKA in PyTango related to enums whih can now be used in a more pythonic way.

Geoff reported he worked on an issue reported by Jean-Luc.

Andy mentioned a tool developed by Stuart James from the ESRF to help to visualize in graphs the different Tango classes involved in a device server from an xmi file. It was suggested to create a new dedicated repository for the development of this kind of tools.

Some useful tools developed in the other institutes could be added into this repository like a script used by Elettra to configure the polling or a tool used by ALBA to clean up the Database with device servers marked as exported when they actually crashed.

**Action - ESRF** : ESRF will create this repository and inform the community.

A small discussion on Tango V10 took place and tango-project.eu was mentioned during this discussion.

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could use tango-controls.
