# Tango Kernel Follow-up Meeting - 2020/11/26

Held on 2020/11/26 at 15:00 CET on Zoom.

**Participants**:  Reynald Bourtembourg, Damien Lacoste (ESRF), Thomas Braun (byte physics), 
Mateusz Celary, Michal Liszcz (S2Innovation), Vincent Hardion, Wilmer Nilsson (MaxIV), Anton Joubert (SARAO)
Thomas Juerges (LOFAR), Jairo Moldes, Sergi Rubio (ALBA), Lorenzo Pivetta (ELETTRA)

# Minutes

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2020/2020-10-22/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - Kernel developers**: Look at https://github.com/pulls/review-requested and review/merge pending PRs

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the 
TangoSourceDistribution repository.

**Action - All**: Test [9.3.4](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4) release.  

**Action - ESRF (Andy)**: Create an issue (in TangoTickets) to transmit a more meaningful error message when 
Corba Transient Timeout exception are received.

**Action - Sergi**: Check whether the latest Pogo version is fixing an issue regarding dynamic attributes in PyTango High Level API.

**Action - ESRF**: Create News on tango-controls.org website to advertise the 9.3.4 release.
**News has been published**

**Action - S2Innovation (Piotr)**: Contact Emmanuel Taurel to see whether he remembers how to get/set the list of allowed 
commands when a Device is locked.

**Action - byte physics?**: Document GDK_SCALE trick on Tango Source Distribution README

**Action - byte physics?**: Add some information on Tango Source Distribution README about systemd integration

**Action - Andy?**: Update Documentation to give a recipe on how to install Tango with the Tango Source Distribution on Ubuntu

## Tango RFCs

Please refer to https://github.com/tango-controls/rfc/wiki/Meeting-2020-11-26

TL;DR: 
- Piotr has merged the hanging PRs
- Gwenaelle has accepted MultiDevFailed for RFC-9
- Piotr plans to spend at least 12 hours next week on the RFCs to:
  - polish Device Locking section
  - provide a PR for the cache section

## Tango Kernel Teleconf Meeting reorganization

After the Tango Meeting collaboration discussions, a reorganization of the Tango Kernel Teleconf meeting might be needed.

One of the goals of the meeting should be to prioritize the issues and Pull Requests to be reviewed.
At the end of the meeting at least 5 issues and PRs should get flagged with the 'High Priority' label.
To help doing this task, the [Github project Kanban](https://github.com/tango-controls/cppTango/projects/5) view will be 
used again to know easily what are the issues and PRs we should focus on.

To be able to help prioritizing the issues and PRs, a preparation work is required before the meeting.  
The participants should come to the meeting with a relatively good overview of the main current issues and 
think about the issues which should be considered as high priority.
The triage is done during the meeting.

Good candidates for PR to be labelled as 'High Priority' are Pull Requests having already the "Ready for Merge" and 
"Candidate for Backport" labels because this usually indicates that the PR is ready for review and fixes a bug we 
want to see backported in 9.3-backports branch.  
Thomas Braun proposed to focus on the most recent ones first too to ease the process at the beginning.

Some additional PRs and issues have been labelled with the 'High Priority' label during the meeting and corresponding 
cards have been added to the [Github project Kanban](https://github.com/tango-controls/cppTango/projects/5) view.

Anton proposed to have someone sharing his screen with the agenda during the meeting to help following where we are in 
the meeting.

The ideal would be to be able to find a convenient way for the users to vote for a given issue.
Thomas Braun is not in favour of users adding "+1" comments in the issue because it would bring too much distraction.  
One way is to use reactions (Thumb-up) in the description of an issue/PR.
It is then possible to filter the open issues and order them by the number of reactions on the description using the 
following search filter: `is:issue is:open sort:reactions-+1-desc`.
The following link can be used too: https://github.com/tango-controls/cppTango/issues?q=is%3Aissue+is%3Aopen+sort%3Areactions-%2B1-desc

Separate meetings should be triggered for a project specific technical discussions.  
Thomas Braun suggested to have some cppTango weekly meetings with the cpptango developers (and people interested) 
where cpptango specific (organization and technical) topics could be discussed in more details.
The idea would be to block 90 minutes max every week in the agenda of the cpptango developers for such a meeting, ideally 
always on the same day and time.  
If there is nothing to be discussed, the meeting could be cancelled after some simple exchanges on cpptango-dev slack channel.  

## High priorities issues

Here are the high priority issues defined during the previous meetings and which have not yet been solved:

On PyTango, the priority is on the tests passing on Windows.   

The current priorities are: 

- DS hangs when concurrently subscribing to events and destructing DeviceProxy ([pytango#315](https://github.com/tango-controls/pytango/issues/315))
_ Use OmniThreads in MultiDeviceTestContext ([pytango#387](https://github.com/tango-controls/pytango/issues/387))

For cppTango, the priorities can be seen on the [Tango 9 Long Term Support project](https://github.com/tango-controls/cppTango/projects/5) 
Kanban view (issues with "high Priority" Label).
At the end of the meeting, the cppTango high priority issues were:
- Unsubscribe in push_event leads to API_EventTimeout [#686](https://github.com/tango-controls/cpptango/issues/686) 
(In progress, already solved in 9.3-backports branch [#699](https://github.com/tango-controls/cpptango/pull/699).  
Thomas Braun created [#817](https://github.com/tango-controls/cpptango/pull/817) for the forward port to tango-9-lts)
- Safe interworking between read_attribute() and push_event() [#698](https://github.com/tango-controls/cpptango/pull/698) 
- Bugfix/fix abi checking [#755](https://github.com/tango-controls/cpptango/pull/755)
- Function name and line number in logs and exceptions [#742](https://github.com/tango-controls/cpptango/pull/742)
- cppapi/server/jpeg_mmx/jpeg_dct_mmx.cpp: Remove calling GCC internal functions [#783](https://github.com/tango-controls/cpptango/pull/783)
- Fix API_EventTimeOut [#817](https://github.com/tango-controls/cpptango/pull/817)

Reynald added [cpptango#812](https://github.com/tango-controls/cppTango/issues/812) in the list of high priority issues 
after the meeting because something should be done before 31st December on Travis-CI.org migration topic.

## Tango Kernel Webinars

- Webinar on Astor/Starter/Pogo, presented by Pascal Verdier will take place on Wednesday 16th December @ 10:00 CET
- Webinar on cppTango events, presented by Emmanuel Taurel will take place on Wednesday 20th January @ 10:00 CET

After the events on cppTango, the following cppTango webinars could present the singleton classes and the Tango Monitor 
feature (Serialization).

**Action - Reynald**: See with Geoff whether he could present the pybind11 development kernel webinar on 9th December.
**Action - Alba**: See whether Tiago could present a Tango Kernel webinar on pytango (In February?).

## Roadmap (V10, LTS version(s))

Discussions took place on the Long Term Support and V10 development. What branches should be supported in cppTango for 5 years?  
When Tango 9 LTS versions were presented at [ICALEPCS 2017](https://youtu.be/t6L6hj0rNDc?t=534), it was said that Tango 
V9 would be supported for min 5 years from the moment when a Tango V10 stable release will be out.  
In the meantime, 9.3.4 was released and a cpptango 9.4 version (not binary compatible with 9.3.x but source code compatible) 
was planned.
Do we want to support 9.3.x versions for 5 years from the moment when cppTango 9.4 is out or do we focus on cppTango 9.4 
for the long term support?
The Long Term Support strategy and policy must be clarified.

As a potential Corba alternative for V10, Thomas Juerges suggested to have a look at ICE: https://zeroc.com/products/ice

Vincent Hardion suggested to get at least 1 action toward Tango V10 at the end of each Tango Kernel Teleconf Meeting.  
Vincent mentioned that Wilmer Nilsson is working 1day/week on the Tango V10 prototype. He suggested that Wilmer could 
present what he has done and discovered so far while working on the prototype during the next Tango Kernel Teleconf meeting.

**Action - Max IV**: Wilmer will present what he has done, discovered while working on the Tango V10 prototype using 
Google Protobufs. This presentation will take place during the next Tango Kernel Teleconf Meeting on 10th December.

## Travis-ci.org shutdown

This topic was not discussed during this meeting.

**Action - All developers relying on travis-ci.org**: Please comment [cpptango#812](https://github.com/tango-controls/cppTango/issues/812) because something should be done 
before 31st December on Travis-CI.org migration topic.

## Conda packages

This topic was not discussed during this meeting.

Reynald updated the version of a github action used in tango-conda-recipes and pytango-conda-recipes repositories to 
make the Github workflows checks operational again.

Reynald updated tango-test conda recipe for TangoTest 3.1.

## AOB

## Support for device level dynamic attributes ([cppTango#814](https://github.com/tango-controls/cppTango/issues/814))

Sergi said that a technical review is required on https://github.com/tango-controls/cppTango/issues/814.  
He proposes to trigger a meeting with some cppTango experts to discuss the feasibility of what is proposing Henrik Enquist.

**Action - Reynald**: Organize a zoom meeting on the support for device level dynamic attributes and try to see whether 
Emmanuel Taurel could attend too. The meeting link will be shared on tango-controls kernel slack channel.

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

The next Tango kernel Teleconf meeting will take place in 2 weeks on Thursday 10th December 2020 at 15:00 **CET**. 
It will be the last Tango Kernel Teleconf Meeting in 2020.

## Summary of remaining actions

**Action - All institutes**: Please vote (thumb up reaction in the description of the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - Kernel developers**: Look at https://github.com/pulls/review-requested and review/merge pending PRs. 
If possible, please focus on the PR having the 'high priority' label.

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the 
TangoSourceDistribution repository.

**Action - All**: Test [9.3.4](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4) release.  

**Action - ESRF (Andy)**: Create an issue (in TangoTickets) to transmit a more meaningful error message when 
Corba Transient Timeout exception are received.

**Action - Sergi**: Check whether the latest Pogo version is fixing an issue regarding dynamic attributes in PyTango High Level API.

**Action - S2Innovation (Piotr)**: Contact Emmanuel Taurel to see whether he remembers how to get/set the list of allowed 
commands when a Device is locked.

**Action - byte physics?**: Document GDK_SCALE trick on Tango Source Distribution README

**Action - byte physics?**: Add some information on Tango Source Distribution README about systemd integration

**Action - Andy?**: Update Documentation to give a recipe on how to install Tango with the Tango Source Distribution on Ubuntu

**Action - Reynald**: See with Geoff whether he could present the pybind11 development kernel webinar on 9th December.

**Action - Alba**: See whether Tiago could present a Tango Kernel webinar on pytango (In February?).

**Action - Max IV**: Wilmer will present what he has done, discovered while working on the Tango V10 prototype using 
Google Protobufs. This presentation will take place during the next Tango Kernel Teleconf Meeting on 10th December.

**Action - All developers relying on travis-ci.org**: Please comment [cpptango#812](https://github.com/tango-controls/cppTango/issues/812) because something should be done 
before 31st December on Travis-CI.org migration topic.

**Action - Reynald**: Organize a zoom meeting on the support for device level dynamic attributes and try to see whether 
Emmanuel Taurel could attend too. The meeting link will be shared on tango-controls kernel slack channel.
