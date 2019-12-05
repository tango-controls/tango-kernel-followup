# Tango Kernel Follow-up Meeting - 2019/11/26

Held on 2019/11/26 at 13:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants: Andrew Goetz, Reynald Bourtembourg (ESRF), Lorenzo Pivetta, Graziano Scalamera (Elettra), 
Michal Liszcz, Konrad Łata (S2Innovation), Solaris Team, Igor Khokhriakov (IK/HZG), Thomas Braun (Byte Physics),
Goeffrey Mant (STFC), Sergi Rubio (ALBA).

# Minutes

## Tango Source Distribution

tango 9.3.4~rc2 has been accepted into Debian experimental. So it can already be tested on Debian unstable.

News about tango Debian package can be found on the following web page: https://tracker.debian.org/pkg/tango

Tango Source Distribution 9.3.4-rc3 will be prepared and will include the latest versions of the tango software.

**Action - Thomas Braun**: Ping Frédéric Picca to get an update on the status and to know whether some help from us is required.

## cppTango News

### Stalled Pull Requests

- Questions raised in [#504](https://github.com/tango-controls/cppTango/pull/504) (PR to fix #368): Pushing events for State and Status with quality factor and timestamp.

It was agreed during the meeting to throw an exception if a user is trying to push an event for _State_ or _Status_ 
using a push_xxx_event method passing a quality factor as parameter.
The quality factor for _State_ and _Status_ attributes should always be set to VALID.

It was also agreed that there should be a way to provide a custom state/status value and timestamp when pushing events for _State_ or _Status_ attributes.

- [#551](https://github.com/tango-controls/cppTango/pull/551)) to implement the server_init_hook() feature. 
Changes were requested during Thomas Braun's review. Please comment on Github to move forward.
- [#480](https://github.com/tango-controls/cppTango/pull/480): DevEnum Support for commands. 
This one requires a change in the IDL. Since we already said cppTango 9.4 won't be binary compatible with cppTango 9.3, there is no problem to merge this one in tango-9-lts once reviewed properly. 

Reynald Bourtembourg created [cppTango#552](https://github.com/tango-controls/cppTango/pull/552) to fix a bug which could lead 
to a crash when reading a forwarded state attribute. This PR needs to be reviewed too.

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.
**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

Thomas Braun asked to clarify the PR merge policy. 
Up to now, the implicit merging policy was that a Pull Request had to be reviewed by at least Reynald Bourtembourg to be allowed to be merged. 
There is a proposal to change that and to allow the merging of some Pull Requests even when Reynald had no time to review it.
Reynald said that simple Pull Requests (like fixing a typo in a comment/documentation) can be merged by anyone.
Normal Pull Requests should be approved by at least 2 cppTango kernel developers.

**Action - Thomas Braun**: Thomas will prepare a Pull Request documenting the contribution process and merging policy.

## JTango News

JTango 9.5.18, fixing an issue occurring when a Java application is subscribing to a big number of events, has been released 
and will be included in Tango Source Distribution 9.3.4-rc3.

Sergi reported an issue with the events and astor when using network aliases. 
This is probably the same issue as what has been solved in cppTango 9.3.3.
The same kind of solution should be implemented in JTango.

**Action - ESRF**: Contact Gwenaëlle to see whether Soleil could implement this fix. 

Igor mentioned a problem with some random timeout issues (Igor, please add more details here).

**Igor**: 

Running this simple code snippet will almost 100% sure fail with CORBA.Timeout:

```java
@Test
@Ignore
public void testTimeout() throws Exception{
    TangoAttribute attr = new TangoAttribute("development/test_server/0/double");

    for(int i = 0; i<1_000_000; ++i) {
        System.out.println(attr.read());
    }
}
```

TestServer project is located here: https://github.com/Ingvord/tango-test-server

TestServer is launched on a different machine within the network. Having 2 clients greatly improves probability of the timeout

## PyTango News

Geoff Mant reported on the migration from Boost to PyBind11. 
The basic server & client code implementation is complete.
A Python HL version of TangoTest was written for unit testing.
The python code has been updated to version 9.3.
* Unit tests completed for:
    * commands 
    * attributes
    * pipes (read + write)
    * polled events
    * device_data
    * attribute_proxy

* Unit tests required for:
    * device_proxy (80% complete)
    * properties
    * database
    * push_events (pipe_events complete)
    * callbacks
    * groups
    * forwarded attributes
    
The development is done on [pytango pybind11 branch](https://github.com/tango-controls/pytango/tree/pybind11).

**Action - Geoff**: Push the latest developments to [pytango pybind11 branch](https://github.com/tango-controls/pytango/tree/pybind11) on Github tango-controls pytango repository.

Alba is currently testing some PyTango Pull requests. 

## High priorities issues

Graziano Scalamera asked to raise the priority for [cppTango#511]((https://github.com/tango-controls/cppTango/issues/511))

**Action - cppTango team**: coordinate on slack to decide who will work on [cppTango#511]((https://github.com/tango-controls/cppTango/issues/511)) issue. 

**Action - All**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would 
like to get solved first.

## AOB

### Tango on Docker
* S2Innovation is working together with SKA on improving SKA's Docker containers (https://gitlab.com/ska-telescope/ska-docker).
  They propose to publish SKA images to official Tango Docker Hub (https://hub.docker.com/u/tangocs)
  so that community can easily find and use these images.
* Following Docker images are available:
    * ska-python-buildenv,
    * ska-python-runtime,
    * tango-builder,
    * tango-cpp,
    * tango-db,
    * tango-dependencies,
    * tango-dsconfig,
    * tango-itango,
    * tango-java,
    * tango-pogo,
    * tango-rest,
    * tango-starter

More detailed technical discussions (automation, support, image names, build from source distribution or directly from project git repositories?, ...) are required before to decide whether these docker images should be published to the official 
Tango docker hub.

**Action - S2Innovation**: S2Innovation will call for a technical meeting dedicated to these SKA docker images. 
The tango kernel developers, some SKA members and S2Innovation (at least) will be invited.

### Issue with systemd limits and Starter systemd script

Reynald reported an issue they have faced at the ESRF last week where some device servers were receiving some "resource temporarily unavailable" errors 
and the Starter was complaining about some thread creation errors.
This was occurring on a host were many device servers were running, among them there were several multichannel device servers (which are clients to many other devices).

The solution found was to add the following in /etc/systemd/system/tango-starter.service :

```
[Service]
TasksMax=infinity
```

The default TasksMax on Debian Stretch seems to be 4915. 
After moving this setting to infinity, we observed the number of tasks created by the Starter and the processes started by the Starter went above 5000.

The current number of tasks (and the configured limit if not set to unlimited) can be seen from the `systemctl status tango-sarter` command which will display something like:

```
tango-starter.service - ESRF unit service for manage tango init server (Starter)
   Loaded: loaded (/etc/systemd/system/tango-starter.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2019-10-01 12:58:32 CEST; 1 months 25 days ago
 Main PID: 1189 (Starter)
    Tasks: 206 (limit: 4915)
   CGroup: /system.slice/tango-starter.service
           ├─ 1234 /opt/os/bin/Starter test
           ├─ ...
```

This might solve the issue with the Starter reported by ALBA during the previous Kernel Teleconf meeting too.

### Forum
**Action - ALBA**: Help user asking some questions about skippy device server. Done immediately after the meeting. Thanks Sergi**s**!

### Next teleconf meetings

Lorenzo suggested to fix a regular weekday and time for the Tango Kernel teleconf meeting.

**Action - ESRF**: Send a Doodle-like survey to decide on the best weekday and time for regular Tango Kernel meetings.

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2019-11-15/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would 
like to get solved first.

**Action - All**: Test [9.3.4-rc2](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc2) release.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the TangoSourceDistribution repository.

**Action - S2Innovation**: Piotr said he will take care of the documentation issues reported while preparing this 9.3.4 Tango source distribution release.
Piotr will also update the Tango documentation to add links to rpm files created/used by Max IV. 

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - JTango team**: Investigate openjdk7 install failure on Travis

**Action - JTango team**: Release a new version of JTango and describe better the problem which has been solved, in the release notes. Release done. Release description could be improved.

**Action - TangoSourceDistribution team**: Use this new JTango release in 9.3.4 source distribution release.

**Action - All**: Please provide your availability in this [Framadate](https://framadate.org/JNHcEkDDOWl5lgOF) to help decide on the next meeting date and time. Done. Thanks for the ones who participated.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - S2Innovation**: Michal Liszcz will ping Zbigniew Reszela about the issue [pytango#292](https://github.com/tango-controls/pytango/pull/292) and see whether [pytango#315](https://github.com/tango-controls/pytango/pull/315) is due to a similar problem.

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could 
use tango-controls.

**Action - cppTango developers and volunteers**: Review [cppTango#551](https://github.com/tango-controls/cppTango/pull/551), 
[cppTango#555](https://github.com/tango-controls/cppTango/pull/555) and 
[cppTango#552](https://github.com/tango-controls/cppTango/pull/552) Pull Requests

## Summary of remaining actions

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would 
like to get solved first.

**Action - All**: Test [9.3.4-rc2](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc2) release.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the TangoSourceDistribution repository.

**Action - S2Innovation**: Piotr said he will take care of the documentation issues reported while preparing this 9.3.4 Tango source distribution release.
Piotr will also update the Tango documentation to add links to rpm files created/used by Max IV. 

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - JTango team**: Investigate openjdk7 install failure on Travis

**Action - ESRF**: Update JTango 9.5.18 release notes to better describe the problem which has been solved.

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

**Action - ESRF**: Contact Gwenaëlle to see whether Soleil could implement this fix. 

**Action - Geoff**: Push the latest developments to [pytango pybind11 branch](https://github.com/tango-controls/pytango/tree/pybind11) on Github tango-controls pytango repository.

**Action - cppTango team**: coordinate on slack to decide who will work on [cppTango#511]((https://github.com/tango-controls/cppTango/issues/511)) issue.

**Action - S2Innovation**: S2Innovation will call for a technical meeting dedicated to these SKA docker images. 
The tango kernel developers, some SKA members and S2Innovation (at least) will be invited.

**Action - ESRF**: Send a Doodle-like survey to decide on the best weekday and time for regular Tango Kernel meetings.
