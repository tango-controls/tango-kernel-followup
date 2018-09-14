# Tango Kernel Follow-up Meeting - 2018/09/14

Held on 2018/09/14 at 14:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants: Reynald Bourtembourg, Andrew Goetz (ESRF),  Igor Khokhriakov (HZG-IK), ...


# Minutes
## 1. cppTango News (cppTango 9.3.2rc, SonarQube, coverall, backports from Tango 10 development branch, ...)
cppTango 9.3.2 has been (pre-)released this week. It is installed on parts of the ESRF control system since Tuesday 11th September 2018. No problem reported so far. Please test this version if you can.

Igor integrated SonarQube and Coverall in cppTango.

## 2. Windows support (VS2017support, appveyor artefacts retention policy, Solaris contribution...)

appveyor builds have been repaired thanks to the work done by Sébastien Gara and Reynald Bourtembourg.

We will need to agree on a limited list of MSVC compilers to put in the automatic builds to avoid to slow them down too much. It is possible to build for all the old compilers and new compilers after every commit/PR, using APPVEYOR_BUILD_WORKER_IMAGE tweak variable as described in appveyor documentation (https://www.appveyor.com/docs/build-environment/#using-multiple-images-for-the-same-build) but we should still limit the number of compilers used for each build to speed up the builds.

## 3. Tango Source Distribution (Solaris contribution)

## 4. Next Tango kernel and documentation meeting (where and when?)

## 5. Go through the main issues and define priorities

## 6. Waltz new release deployment at ESRF

## 7. JetBrains OS license renewal

## 8. TangoBox status

## 9. AOB (JTango?, PyTango?, ...?)

## 7. Status of Actions defined in the previous meetings:

The following tasks had been defined during the previous meetings:

**Action - ESRF**: ESRF will send an e-mail to tango-controls info mailing list and post a message on the forum to try to get some feedback from the users to know whether the old compilers support is still required.

The e-mail was sent and a new topic was posted on the forum. We got some feedback from users who need support for msvc9 and win32-msvc12.

**Action - ALBA** from previous teleconf meeting: ALBA will create a ticket in TangoTicket to request the possibility to specify the ports used by ZMQ.

**Action - Solaris**: Solaris will create a Doodle (or similar) to define place and/or dates.

**Action - ESRF** : ESRF will create a repository (organization?) to host tango related tools which might be interesting for the community. ESRF will then inform the community.

The following github organization has been created for this purpose: https://github.com/tango-controls-tools and an e-mail has been sent to tango-controls info mailing list.

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could use tango-controls.
