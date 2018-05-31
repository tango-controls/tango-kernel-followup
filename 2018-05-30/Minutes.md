# Tango Kernel Follow-up Meeting - 2018/05/30

Held on 2018/05/30 at 16:00 CET on https://appear.in/tango-kernel

Participants: Reynald Bourtembourg, Andrew Goetz, Jean-Michel Chaize (ESRF)
              Igor Khokhriakov (IK), Geoffrey Mant (STFC),
              Sergi Rubio, Jairo Moldes (ALBA)

# Minutes
## 1. New Github repository to archive the Tango kernel meeting minutes: https://github.com/tango-controls/tango-kernel-followup

Everyone agreed to use github for minutes

## 2. cppTango 9.3.0 and 9.3.1 pre-release status and issues.

Reynald asked if any sites still have a large number of V7 device servers and clients. ALBA is still using V7 for most device servers running on Suse 11. They tried V9 and could compile the C++ kernel but there was a problem with PyTango V9. In order to upgrade they need to upgrade the hardware

It would help if the zmq port for sending events from a device server could be fixed. ALBA will make a feature request for this.

It is essential to fix Tango v9.3.x clients subscription to Tango V7.x servers. Some sites (ALBA) still using notifd.

Reynald warned about the issues related to events compatibility (with Tango 7 and 8) and dynamic attributes introduced in cppTango 9.3.0 and 9.3.1. The issue related to dynamic attribute has been solved in tango-9-lts branch. Reynald advised to wait for a cppTango version where backwards-compatibility for the event system is working as expected.

Jairo mentioned they have seen issues with the ZMQ version used at ALBA. Reynald advised to use the patch from https://github.com/tango-controls/cppTango/pull/445 to solve this issue.

## 3. Tango Meeting preparation

Announce the documentation session on email and website.

Reduce the documentation tutorial.

Announce in advance topics for Tango brainstorming. Maybe providing short description of each topic e.g. *blockchain* -- append only linked list that uses hash pointers; *serverless* - an architecture principle when hardware is separated from software. So people can think about it before brainstorm session.

Reynald will present a slide introducing very briefly the work done by Sergi on HDB++. More details will be given by Sergi in his talk.

## 4. Go through the main issues and define priorities

Members of ALBA mentioned the problem they have with ZMQ and the fact that we currently cannot tell to ZMQ to use predefined ports. This is a problem for ZMQ events to go through firewalls.
*Action*: ALBA will create an issue on TangoTickets Github repository.

The highest priority is currently to solve the issues related to events compatibility with Tango 7 and 8.

Give the possibility to fix ZMQ ports is also a priority for sites like ALBA.

## 5. AOB (JTango?, PyTango?, ...?)

Sergi said he is currently working on the HDB++ Cassandra support in PyTangoArchiving in order to support the latest versions of the HDB++ Cassandra schema.
PyBind11: Geoff mentionned he has done some progress on the client side.
