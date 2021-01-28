# Tango Kernel Follow-up Meeting - 2021/01/28

Held on 2021/01/14 at 15:00 CET on Zoom.

**Participants**:  Benjamin Bertrand (MaxIV), Reynald Bourtembourg, Andrew Goetz, Damien Lacoste (ESRF), 
Thomas Braun (byte physics), Mateusz Celary, Michal Liszcz (S2Innovation),  Anton Joubert (SARAO), 
Thomas Juerges (LOFAR), Sergi Rubio (ALBA), Lorenzo Pivetta (ELETTRA), Stephane Poirier (SOLEIL), Sonja Vrcic (SKAO)

# Minutes

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2021/2021-01-14/Minutes.md#summary-of-remaining-actions)

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the
TangoSourceDistribution repository. Move spec rpms repository to gitlab.com/tango-controls
**Benjamin proposes to have a separate repository for the spec rpms. He did some tests with [Copr](https://copr.fedorainfracloud.org).
Copr keeps only the last [ones](https://copr.fedorainfracloud.org/coprs/g/tango-controls/tango/builds/). Thomas Braun proposes to store the binaries with Gitlab 
([Generic packages on Gitlab](https://gitlab.com/gitlab-org/release-cli/-/tree/master/docs/examples/release-assets-as-generic-package/)).
*** He also sent this link on Kernel slack channel related to showing an issue "Investigate how to add support for RPM to 
the Package Registry" : https://gitlab.com/gitlab-org/gitlab/-/issues/296785 . 
The spec rpm repo should be moved to gitlab.com/tango-controls**

-  2021/01/28 update: rpm packages have built, links to be provided

- Piotr manifests Soleil's interest in rpm packages, although nobody from Soleil is present, so they will be contacted for testing

**Action - All institutes**: Please vote (thumb up reaction in the description of the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - Kernel developers**: Look at https://github.com/pulls/review-requested and review/merge pending PRs.
If possible, please focus on the PR having the 'high priority' label.

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - ESRF (Andy)**: Update the description of issue https://github.com/tango-controls/cppTango/issues/822

**Action - Andy?**: Update Documentation to give a recipe on how to install Tango with the Tango Source Distribution on Ubuntu

**Action - ESRF (Andy)**: Ask Webu how much it would cost if they would maintain a Gitlab instance on tango-controls.org domain?

**Action - All**: Be prepared to discuss the priorities of the open Pull Requests and Issues at the coming Tango Kernel Teleconf meeting.
**Reynald should send a reminder several days before the meeting**

**Action: Reynald**: Inform his colleagues about the migration for repositories like jive, atkpanel, astor, Starter, etc...

**Action - Sergi**: Organize a meeting with Anton, Zibi and Sergi on the DeviceProxy destruction topic.

**Action - Andy**: Contact Geoff to see when he could present a Kernel Webinar on pybind11.

**Action - Gitlab Migration**: See actions and proposals below


---

## Gitlab migration ([TangoTickets#47](https://github.com/tango-controls/TangoTickets/issues/47))

There has been a Tango Steering Committee meeting on Tuesday 15th December 2020. 
It has been decided to migrate from Github to Gitlab.

Andy applied for Gitlab.com gold license.
tango-controls has been granted a Gitlab.com gold license for 100 seats and 1 year.

All the migration details can be found and commented on https://github.com/tango-controls/TangoTickets/issues/47.

The first repositories who have announced a migration date are the following:

- itango: migration planned on Thursday 21th January
- cppTango : migration planned on Thursday 21th January
- pytango: migration planned on Thursday 28th January

Mateusz will help with pytango CI migration to gitlab-ci. Alberto Lopez from Alba has already started some work on that topic.

Sergi will ensure Mateusz, Anton and the new recruit are in touch to avoid duplication of the work.

Andy will check with Piotr for the JTango CI part?

On cppTango side, Michal has created [cppTango#820](https://github.com/tango-controls/cppTango/pull/820) to convert Travis CI to Gitlab CI on tango-9-lts branch.
The same will be done for 9.3-backports branch ([cppTango#825](https://github.com/tango-controls/cppTango/pull/825)).

Following a suggestion from Thomas Braun, it has been decided to remove bintray integration in cpptango and to rather 
use Gitlab package registry.

Michal created [cpptango#821](https://github.com/tango-controls/cppTango/issues/821) to track what should be done after the migration.

**Action: Reynald**: Inform his colleagues about the migration for repositories like jive, atkpanel, astor, Starter, etc...

**Action: Sardana**: Sardana team has decided to not migrate yet

**Proposal: Thomas**: A message will be added to announce that projects has been moved and the current code moved to archiving in github, it is proposed to add a PR to remove the CI/CD code to make people aware that no longer builds will be provided from github.
*** Lorenzo proposed to fully remove the repository, but it may cause issues as many projects are still linked to this project and many links would be broken for people not aware of the move.

**Proposal: Carlos**: proposal to rename or remove the default branch but to keep the rest of the branches for all the people working in parallel developments or tags.

Decission to be taken:

 - erase completely (only lorenzo agrees)
 - create new branch with just a README and leave it as default branch on github
 - move branches code to github archiving, so will not be updated anymore and will not become a fork
 

***

## High priorities issues

The main bocking issue for pyTango is the one related to the DeviceProxy destruction.

**Action - Sergi**: Organize a meeting with Anton, Zibi and Sergi on the DeviceProxy destruction topic.
***Pending***: Sergi will organize the meeting during the next week

In cppTango, the Gitlab migration is top priority.

Reynald wanted to add https://github.com/tango-controls/cppTango/pull/729 in the High Priority issues.

For cpptango, you can refer to this [Kanban board](https://github.com/tango-controls/cppTango/projects/5) to know what 
are the Pull Requests which are currently missing some review approvals.  
_In theory_, the ones which are labeled _easy to review_ should be easier to review, so please, even if you're not a Tango 
kernel developer, you can help in reviewing these PRs.

**Action - All**: Be prepared to discuss the priorities of the open Pull Requests and Issues at the coming Tango Kernel Teleconf meeting.

## Conda recipes

Benjamin submitted a PR to get the tango conda packages available in conda-forge conda channel.
Thanks to this, we will benefit from conda-forge infrastructure and we will get more versions of each conda package, 
and we will limit the risk of conflicts.  
Thanks Benjamin for this initiative!

## Tango Kernel Webinars

- Webinar on cppTango events, presented by Emmanuel Taurel will take place on Wednesday 20th January @ 10:00 CET

Sergi talked to Tiago about the PyTango webinar. Tiago doesn't trust is memory enough to present a webinar on pyTango.

**Action - Reynald**: Send an e-mail on info tango-controls mailing list to advertise the coming webinar.  **Done**
**Action - Andy**: Contact Geoff to see when he could present a Kernel Webinar on pybind11.

## AOB

### pytango 9.3.3

ESRF has installed pytango 9.3.3 during this winter shutdown.  
Alba is already using pyTango 9.3.3 as well on some systems.  
ESRF is still validating pytango on Power9 architecture. 

Sergi mentioned that they are experiencing a memory leak issue when using pytango 9.3.3 and older when reading states of
devices in a thread.

### Next teleconf meeting

Tango Kernel Teleconf Meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

So the next Tango Kernel Teleconf Meeting will take place on Thursday 28th January 2021 at 15:00 **CET**. 

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

**Action - Max IV**: Move spec rpms repository to gitlab.com/tango-controls

**Action - ESRF (Andy)**: Update the description of issue https://github.com/tango-controls/cppTango/issues/822

**Action - Andy?**: Update Documentation to give a recipe on how to install Tango with the Tango Source Distribution on Ubuntu

**Action - ESRF (Andy)**: Ask Webu how much it would cost if they would maintain a Gitlab instance on tango-controls.org domain?

**Action - All**: Be prepared to discuss the priorities of the open Pull Requests and Issues at the coming Tango Kernel Teleconf meeting.
**Reynald should send a reminder several days before the meeting**

**Action: Reynald**: Inform his colleagues about the migration for repositories like jive, atkpanel, astor, Starter, etc...

**Action - Sergi**: Organize a meeting with Anton, Zibi and Sergi on the DeviceProxy destruction topic.

**Action - Andy**: Contact Geoff to see when he could present a Kernel Webinar on pybind11.

