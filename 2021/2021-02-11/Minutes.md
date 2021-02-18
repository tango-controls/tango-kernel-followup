# Tango Kernel Follow-up Meeting

Held on 2021/02/11 at 15:00 CET on Zoom.

**Participants**:
- Andrew Goetz (ESRF)
- Benjamin Bertrand (MaxIV)
- Gwenaelle Abeillé (SOLEIL)
- Lorenzo Pivetta (ELETTRA)
- Michal Liszcz (S2Innovation)
- Nicolas Leclercq (ESRF)
- Piotr Goryl (S2Innovation)
- Reynald Bourtembourg (ESRF)
- Sergi Rubio (ALBA)
- Thomas Braun (byte physics)
- Vincent Hardion (Max IV)

(and some people Thomas has forgotten, as he was not aware of recording that list)

# Minutes

## Status of [Actions defined in the previous meetings](../2021-01-28/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Please vote (thumb up reaction in the description of the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - Kernel developers**: Look at https://github.com/pulls/review-requested and review/merge pending PRs.
If possible, please focus on the PR having the 'high priority' label.

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action -  Sergi**: tangocpp PR 742 (on names on logs) to be reviewed

**Action - Max IV**: provide links to spec rpms repository
Done

**Action - ESRF (Andy)**: Update the description of issue https://github.com/tango-controls/cppTango/issues/822

**Action - Andy?**: Update Documentation to give a recipe on how to install Tango with the Tango Source Distribution on Ubuntu

**Action - ESRF (Andy)**: Ask Webu how much it would cost if they would maintain a Gitlab instance on tango-controls.org domain?
Postponed indefinitly, we don't want to move again.

**Action - All**: Be prepared to discuss the priorities of the open Pull Requests and Issues at the coming Tango Kernel Teleconf meeting.
**Reynald should send a reminder several days before the meeting**

**Action: Reynald**: Inform his colleagues about the migration for repositories like jive, atkpanel, astor, Starter, etc...
Done.

**Action - Sergi**: Organize a meeting with Anton, Zibi and Sergi on the DeviceProxy destruction topic.
Investigation is still ongoing.

**Action - Andy**: Contact Geoff to see when he could present a Kernel Webinar on pybind11.
Vincent is also reaching out to his colleagues for presenting on pytango

 **Action - Cpascual**: create new branch with just a README and leave it as default branch on github (everyone agrees)

**Action - Cpascual**: move branches code to github archiving, so will not be updated anymore and will not become a fork (everyone agrees)
Done.

**Action: cppTango migration**: to be done after the meeting
Done.

**Action: itango migration**: to be done tomorrow
Done.

**Action - TANGO RFCs Migration: Piotr**: Collecting the lists of members to be notified, preparing pdf's from the main branch to be made available.
Done.

**Action - Reynald**: share the knowledge got after discussing with Emmanuel Taurel about how the last Tango Windows distribution was created.
I should share that on https://github.com/tango-controls/TangoTickets/issues/37

**Action - Sergi**: debug a memory leak issue when using pytango 9.3.3 and older when reading states of devices in a thread.
Ongoing, (note: please add a issue link)

## Gitlab migration

- cppTango/itango/pytango/TangoSourceDistribution migration is done
- RFC repo is prepared for migration
- Remaining planned migrations are under actions

## JTango migration

Bintray is being shutdown. cpptango uses it, but is planning to migrate away from it. JTango depends on bintray and that
is discontinued, gitlab supports maven repositories, see https://docs.gitlab.com/ee/user/packages/maven_repository/ but
only for java 11, but java 8 is required as well.

## Tango RFCs

- Migration to gitlab is immanent
- scripts will be added for PDF generation, there will be a single PDF file
- readthedocs HTML is also requested, Benjamin Bertrand will supply some script to Piotr for MD-\>HTML conversion

## conda recipes

Work is ongoing to create a separate cppTango package which hold debug symbols. https://github.com/conda-forge/cpptango-feedstock/pull/2

## cppTango: branch organization
(Question from Thomas B.): Is it still desired that we actively manage two branches: 9.3-backports and tango-9-lts? The current approach
is that both are managed and 9.3-backports would also be the source of 9.3.5 which is just 9.3.4 with fixes.

- Many opinions, everyone is using 9.3.4, nobody is using 9.4.x from tango-9-lts
- Lorenzo likes 9.3.x because it can be compiled on legacy platforms like powerpc
- Reynald proposes that once 9.4.0 is released, 9.3-backports branch will not be activly developed anymore, we might
  still accept bugfix PRs
- 9.3-backports will keep using appveyor, tango-9-lts will be trying gitlab runners
- Vincent proposes to communicate how we support each version
- We (tango controls) communicated that we support 9.3 for 5 years, 9.3.0 came out in May 2018
- Sergey says that the LTS period should only start once V10 (which might not be able to speak to tango < 10)

Conclusion:
  - Rename tango-9-lts to main, rename master to tango-v10
  - Backport important bugfixes from main to 9.3-backports
  - Continue releasing 9.3.X versions with bugfixes from 9.3-backports
  - Once 9.4 is released from main, we reconsider how we can support 9.3-backports

### Next teleconf meeting

Tango Kernel Teleconf Meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

So the next Tango Kernel Teleconf Meeting will take place on Thursday 25th February 2021 at 15:00 **CET**.

## Summary of remaining actions

**Action - All institutes**:
Please vote (thumb up reaction in the description of the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - Andy (ESRF)**:
Update the description of issue https://github.com/tango-controls/cppTango/issues/822

**Action - Andy (ESRF)**:
Update Documentation to give a recipe on how to install Tango with the Tango Source Distribution on Ubuntu

**Action - Andy (ESRF)**:
Contact Geoff to see when he could present a Kernel Webinar on pybind11.

**Action - Benjamin B.**:
Try out gitlab runners on windows for pytango

**Action - Benjamin B.**:
Supply script to Piotr for MD-\>HTML conversion used for tango RFCs

**Action - Reynald**:
Share the knowledge, after discussing with Emmanuel Taurel, about how the last Tango Windows distribution was created.
https://github.com/tango-controls/TangoTickets/issues/37

**Action - Reynald**:
Create ticket in cppTango for RelWithDebInfo, see CMAKE_BUILD_TYPE, https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html

**Action - Reynald**:
Look at old cppTango PRs targeting `tango-v10`, and comment/close/create issue

**Action - Sergi**:
tangocpp PR 742 (on names on logs) to be reviewed

**Action - Sergi**: debug a memory leak issue when using pytango 9.3.3 and older when reading states of devices in a thread.
Ongoing, (note: please add a issue link)

**Action - Sergi**:
Organize a meeting with Anton, Zibi and Sergi on the DeviceProxy destruction topic. Investigation is still ongoing.

**Action - Thomas B.**:
Gitlab migration:
 * https://github.com/tango-controls/tango_admin
 * https://github.com/tango-controls/TangoDatabase
 * https://github.com/tango-controls/starter
 * https://github.com/tango-controls/docker-mysql
 * https://github.com/tango-controls/TangoTest-docker
 * https://github.com/tango-controls/tango-libs-docker

See also https://github.com/tango-controls/TangoTickets/issues/47

**Action - Thomas B.**:
Try out the gitlab runners on windows which are in beta phase from gitlab

**Action - Thomas B.**:
Rename cppTango branches and update Readme.md/HowToContribute.md

**Action - Thomas B.**:
Remove "Ready for Merge" label and convert existing MRs into draft mode. Document how we use these labels in
HowToContribute.md

**Action - Vincent**:
Reach out to colleagues for presenting pytango on tango kernel webinar
