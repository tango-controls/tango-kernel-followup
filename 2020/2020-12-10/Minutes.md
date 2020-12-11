# Tango Kernel Follow-up Meeting - 2020/12/10

Held on 2020/12/10 at 15:00 CET on Zoom.

**Participants**:  Antonio Bartalesi, Benjamin Bertrand, Johan Forsberg, Vincent Hardion, Wilmer Nilsson (MaxIV), 
Reynald Bourtembourg, Andrew Goetz, Damien Lacoste (ESRF), Thomas Braun (byte physics), 
Mateusz Celary, Piotr Goryl, Michal Liszcz (S2Innovation),  Anton Joubert (SARAO)
Thomas Juerges, Jan David Mol (LOFAR), Carlos Pascual, Sergi Rubio (ALBA), Lorenzo Pivetta (ELETTRA),
Stephane Poirier (SOLEIL)

# Minutes

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2020/2020-10-22/Minutes.md#summary-of-remaining-actions)

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
**Sergi has tested Pogo. He has created a new ticket with the issues he has found with PyTango and DeviceCommands 
(https://github.com/tango-controls/pytango/issues/396). The rest of features apart of Dynamic Commands seem to work properly.**

**Action - S2Innovation (Piotr)**: Contact Emmanuel Taurel to see whether he remembers how to get/set the list of allowed 
commands when a Device is locked. **Done. Reynald found an answer by looking at the code. He didn't test it.**

**Action - byte physics?**: Document GDK_SCALE trick on Tango Source Distribution README.  
**Done by Thomas in [tds#94](https://github.com/tango-controls/TangoSourceDistribution/pull/94)**

**Action - byte physics?**: Add some information on Tango Source Distribution README about systemd integration.   
**Done by Thomas in [tds#94](https://github.com/tango-controls/TangoSourceDistribution/pull/94)**

**Action - Andy?**: Update Documentation to give a recipe on how to install Tango with the Tango Source Distribution on Ubuntu

**Action - Reynald**: See with Geoff whether he could present the pybind11 development kernel webinar on 9th December.
**Reynald sent an e-mail. No answer yet, so it probably meant that Geoff was not interested by this free time slot and would like 
more time to prepare the webinar on pybind11?**

**Action - Alba**: See whether Tiago could present a Tango Kernel webinar on pytango (In February?).
**Sergi talked to Tiago. He will try to prepare something for February.
If you have special requests for this PyTango webinar content, please contact Sergi Rubio or Tiago Coutinho from ALBA**

**Action - Max IV**: Wilmer will present what he has done, discovered while working on the Tango V10 prototype using 
Google Protobufs. This presentation will take place during the next Tango Kernel Teleconf Meeting on 10th December.
**Presentation done by Wilmer. Thanks!**

**Action - All developers relying on travis-ci.org**: Please comment [cpptango#812](https://github.com/tango-controls/cppTango/issues/812) 
because something should be done before 31st December on Travis-CI.org migration topic.

**Action - Reynald**: Organize a zoom meeting on the support for device level dynamic attributes and try to see whether 
Emmanuel Taurel could attend too. The meeting link will be shared on tango-controls kernel slack channel.
**Meeting done last week. Thanks Emmanuel Taurel for attending.  
Minutes are online: https://github.com/tango-controls/tango-kernel-followup/blob/master/2020/2020-12-03/Minutes.md**

## Tango GRPC protocol

Wilmer presented the work he has been doing on trying to replace CORBA in cppTango with GRPC.

**Action - MaxIV (Wilmer)**: Make the code of the GRPC prototype publicly available and communicate the link to the Tango 
Kernel developers so they could have a deeper look at the code and give advices and help. Thomas also suggested 
to document the project to help testers/reviewers/contributors to compile and better understand the current code.

## Tango RFCs

Please refer to https://github.com/tango-controls/rfc/wiki/Meeting-2020-12-10

## Travis-ci.org shutdown ([cppTango#812](https://github.com/tango-controls/cppTango/issues/812))

There will be a Tango Steering Committee meeting on Tuesday. The migration from Travis will be one of the discussed topics.

Lorenzo summarized the situation there: 
https://github.com/tango-controls/tango-kernel-followup/blob/master/2020/2020-12-03/Minutes.md#travis-ciorg-shutdown--migration-to-travis-cicom-812

Carlos is suggesting to move to gitlab.com and to apply for the gold licence. 
Thomas warned that some of the features from Gitlab available with a gold account are using proprietary SW from Gitlab.  
Carlos said that we should avoid using these features, which is not always easy because they are not clearly identified as 
proprietary features when you use them.

Andy applied for a free of charge Gold licence on gitlab.com for Tango during the meeting. There should be an answer between 5 to 10 days from now.  
Reynald mentioned that Travis files should be migrated before the end of next week (before the school holidays) if we 
don't want any interruption in our CI process.

An option could be to move to github actions (still free for the moment) to buy us some time before an eventual migration 
to Gitlab (Gitlab.com or self-hosted) in next months.

Reynald did also a small test this week, migrating cppTango to gitea, which is free SW github-like clone 
which can be self-hosted too. The result of the migration can be seen here: https://try.gitea.io/bourtemb/cppTango   
The repository might disappear at any time because it is on a test instance.

So we'll wait for GL feedback on the project status request.  
But it may take some time, and likely not come in time for the next EC meeting. 
The short term action, which implies the less work, seemed to be setting up GH actions by the end of week #51 for the 
projects in trouble with Travis... 

**Action - ESRF (Andy)**: Ask Webu how much it would cost if they would maintain a Gitlab instance on tango-controls.org domain?

## High priorities issues

Due to the length of this meeting, it was not possible to spend much time defining High-Priority issues and Pull Requests, 
contradicting what was said in the previous meeting.

1 High priority issue and its associated PR have been closed/merged in cppTango since the last meeting:
- Unsubscribe in push_event leads to API_EventTimeout ([cppTango#686](https://github.com/tango-controls/cppTango/issues/686))
- Fix API_eventTimeOut ([cppTango#817](https://github.com/tango-controls/cppTango/pull/817))

For cpptango, you can refer to this [Kanban board](https://github.com/tango-controls/cppTango/projects/5) to know what 
are the Pull Requests which are currently missing some review approvals.  
_In theory_, the ones which are labeled _easy to review_ should be easier to review, so please, even if you're not a Tango 
kernel developer, you can help in reviewing these PRs. 

To help focussing on a smaller number of PRs, the _High Priority_ Label has been removed from 
[cpptango#698](https://github.com/tango-controls/cppTango/pull/698).

**Action - All**: Be prepared to discuss the priorities of the open Pull Requests and Issues at the coming Tango Kernel Teleconf meeting.

## Tango Kernel Webinars

- Webinar on Astor/Starter/Pogo, presented by Pascal Verdier will take place on Wednesday 16th December @ 10:00 CET
- Webinar on cppTango events, presented by Emmanuel Taurel will take place on Wednesday 20th January @ 10:00 CET

Sergi talked to Tiago about the PyTango webinar (probably in February 2021).
If there are some specific topic you would like Tiago to talk about during the next PyTango Kernel Webinar, please contact 
Tiago or Sergi. 

## AOB

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

Exceptionally, the next Tango kernel Teleconf meeting will **not** take place in 2 weeks. 
So the next Tango Kernel Teleconf Meeting will take place on Thursday 14th January 2020 at 15:00 **CET**. 

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

**Action - Andy?**: Update Documentation to give a recipe on how to install Tango with the Tango Source Distribution on Ubuntu

**Action - All developers relying on travis-ci.org**: Please comment [cpptango#812](https://github.com/tango-controls/cppTango/issues/812) 
because something should be done before 31st December on Travis-CI.org migration topic.

**Action - MaxIV (Wilmer)**: Make the code of the GRPC prototype publicly available and communicate the link to the Tango 
Kernel developers so they could have a deeper look at the code and give advices and help. Thomas also suggested 
to document the project to help testers/reviewers/contributors to compile and better understand the current code.

**Action - ESRF (Andy)**: Ask Webu how much it would cost if they would maintain a Gitlab instance on tango-controls.org domain?

**Action - All**: Be prepared to discuss the priorities of the open Pull Requests and Issues at the coming Tango Kernel Teleconf meeting.