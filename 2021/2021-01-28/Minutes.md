# Tango Kernel Follow-up Meeting - 2021/01/28

Held on 2021/01/28 at 15:00 CET on Zoom.

**Participants**:  Benjamin Bertrand, Vincent Hardion (MaxIV), Reynald Bourtembourg (ESRF), 
Thomas Braun (byte physics), Mateusz Celary, Piotr Goryl, Michal Liszcz (S2Innovation),  Anton Joubert (SARAO), 
Thomas Juerges (LOFAR), Alberto Lopez, Carlos Pascual, Sergi Rubio (ALBA), Sonja Vrcic (SKAO)

# Minutes

## Kernel Teleconf Minutes Edition Rotation

Sergi Rubio Manrique from ALBA will write the minutes for this session.

For the next sessions, the rule will be ...

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2021/2021-01-14/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Please vote (thumb up reaction in the description of the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - Kernel developers**: Look at https://github.com/pulls/review-requested and review/merge pending PRs.
If possible, please focus on the PR having the 'high priority' label.

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - Max IV**: Move spec rpms repository to gitlab.com/tango-controls.
Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the
TangoSourceDistribution repository. Move spec rpms repository to gitlab.com/tango-controls
**Benjamin proposes to have a separate repository for the spec rpms. He did some tests with [Copr](https://copr.fedorainfracloud.org).
Copr keeps only the last [ones](https://copr.fedorainfracloud.org/coprs/g/tango-controls/tango/builds/). Thomas Braun proposes to store the binaries with Gitlab 
([Generic packages on Gitlab](https://gitlab.com/gitlab-org/release-cli/-/tree/master/docs/examples/release-assets-as-generic-package/)).
*** He also sent this link on Kernel slack channel related to showing an issue "Investigate how to add support for RPM to 
the Package Registry" : https://gitlab.com/gitlab-org/gitlab/-/issues/296785 . 
The spec rpm repo should be moved to gitlab.com/tango-controls**

-  2021/01/28 update: rpm packages have built, links to be provided

- Piotr manifests Soleil's interest in rpm packages, although nobody from Soleil is present, so they will be contacted for testing



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


**Action: Reynald**: Inform his colleagues about the migration for repositories like jive, atkpanel, astor, Starter, etc...

**Action: Sardana**: Sardana team has decided to not migrate yet

**Proposal: Thomas**: A message will be added to announce that projects has been moved and the current code moved to archiving in github, it is proposed to add a PR to remove the CI/CD code to make people aware that no longer builds will be provided from github.
*** Lorenzo proposed to fully remove the repository, but it may cause issues as many projects are still linked to this project and many links would be broken for people not aware of the move.

**Proposal: Carlos**: proposal to rename or remove the default branch but to keep the rest of the branches for all the people working in parallel developments or tags.

Decission to be taken:

 - erase completely (only lorenzo agrees)
 - create new branch with just a README and leave it as default branch on github (everyone agrees)
 - move branches code to github archiving, so will not be updated anymore and will not become a fork (everyone agrees)
 
 **Action**: The empty branch will be removed on gitlab; and the name of the new default branch will be discussed after the migration.
 
 - Thomas suggested to use the new branch as **main**, as it seems the current trend
 - The old master branch will become Tango V10 (or something similar)
 
 Other repos will not be forced to follow the same conventions.
 
 Repositories ready for migration:
 
  - cppTango
  - itango
  - pytango
   * pytango having issues with python 3.5 integration (non blocking, PR to be accepted when ready **Action - Alberto and Anton**)
   
**Action Results: Reynald** : Done a test migration, sent a reminder with the people not yet appearing as available on gitlab

**Action: All?** : to be reviewed how to work on Teams/subgroups and who should have owner permissions on the repos (so not everybody)
 - If it is not possible to do it by groups then it will have to be done per-repository (may be a huge work)
 - **Carlos**: on the migration issue, maintainer should appoint the user owners after the migration (automatic migration seems to set everyone as owner)
 
**Action: cppTango migration**: to be done after the meeting

**Action: itango migration**: to be done tomorrow

**Action - TANGO RFCs Migration: Piotr**: Collecting the lists of members to be notified, preparing pdf's from the main branch to be made available.

***

## High priorities issues

The main bocking issue for pyTango is the one related to the DeviceProxy destruction.

**Action - Sergi**: Organize a meeting with Anton, Zibi and Sergi on the DeviceProxy destruction topic.
 - ***Pending***: Sergi will organize the meeting during the next week

**Issue: Reynaild** Some old JTango java clients creating new connections regularly to devices and not freeing them, 
causing too many open files errors on device servers. Fixed updating JTango.

For cpptango, you can refer to this [Kanban board](https://github.com/tango-controls/cppTango/projects/5) to know what 
are the Pull Requests which are currently missing some review approvals.  
_In theory_, the ones which are labeled _easy to review_ should be easier to review, so please, even if you're not a Tango 
kernel developer, you can help in reviewing these PRs.

**Action - All**: Be prepared to discuss the priorities of the open Pull Requests and Issues at the coming Tango Kernel Teleconf meeting.

## Tango Kernel Webinars

**Action - Andy**: Contact Geoff to see when he could present a Kernel Webinar on pybind11.

## AOB

### pytango 9.3.3

**Action - Sergi**: mentioned that they are experiencing a memory leak issue when using pytango 9.3.3 and older when reading states of
devices in a thread.
 -  Reynald mentioned that similar issues were found due to a HW issue with an ethernet interface, detected by faulty ssh's

### Next teleconf meeting

Tango Kernel Teleconf Meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

So the next Tango Kernel Teleconf Meeting will take place on Thursday 11th February 2021 at 15:00 **CET**. 

## Summary of remaining actions

**Action -  Sergi**: PR 742 (on names on logs) to be reviewed

**FROM THIS POINT ... REST OF ACTIONS TO BE UPDATED**

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

