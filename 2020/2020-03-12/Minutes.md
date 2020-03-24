# Tango Kernel Follow-up Meeting - 2020/03/12

Held on 2020/03/12 at 15:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants:  Reynald Bourtembourg (ESRF), Jairo Moldes (Alba), Anton Joubert (SKA-ZA), Lorenzo Pivetta (Elettra), Michal Liszcz (S2Innovation)

# Minutes

## Tango Source Distribution

[TangoSourceDistribution#69](https://github.com/tango-controls/TangoSourceDistribution/pull/69) (check mariadb version) has been merged.

Simply need to update cppTango Changelog, tag cppTango 9.3.4-rc4 and to update TangoSourceDistribution release notes.

9.3.4-rc4 will hopefully be released before the next meeting in 2 weeks.

## cppTango News

### Recent PR merged
Several PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:
- appveyor.yml: Add inline deployment on tag push ([cppTango#602](https://github.com/tango-controls/cppTango/issues/602), [#616](https://github.com/tango-controls/cppTango/pull/616), [#690](https://github.com/tango-controls/cppTango/pull/690))
- CMakeLists.txt: Add option to disable building the test suite ([cppTango#668](https://github.com/tango-controls/cppTango/pull/668))
- Fix omniidl error checks ([cppTango#687](https://github.com/tango-controls/cppTango/pull/687))
- Bump release number ([cppTango#593](https://github.com/tango-controls/cppTango/pull/593))

### New issues
The following issues and pull requests have been created since the last teleconf meeting and are not yet solved:
- API_ZmqFailed exception thrown in ZmqEventSupplier::push_heartbeat_event leads to program termination ([cppTango#691](https://github.com/tango-controls/cppTango/issues/691))

Michal suggested to look for a better fix than just the basic one suggested in [cppTango#691](https://github.com/tango-controls/cppTango/issues/691) comments.
Reynald encouraged Michal to comment on the Github issue to share his interesting ideas.

### Recent developments

[cppTango#593](https://github.com/tango-controls/cppTango/pull/593) has been rebased and is currently being reviewed. 
Reynald tested it and noticed a remaining issue with the pipe events after the execution of RestartServer admin device command.
It was agreed during the meeting that this will be handled in another PR.

**Action - S2Innovation**: Create a new cppTango issue to track the problem mentioned while reviewing [cppTango#593](https://github.com/tango-controls/cppTango/pull/593).
 Issue with missing pipe events when RestartServer is called. 

## JTango News

No news since the last meeting.

## PyTango News

The new release has been slightly delayed.

There was some progress in the investigations of the deadlocks in python3 when concurrently subscribing to events and destructing DeviceProxy objects ([pytango#315](https://github.com/tango-controls/pytango/issues/31).
There are strong suspicions on the python GIL. 
Jairo Moldes and Tiago Coutinho are trying to reimplement DeviceProxy in order to force the release of the GIL while unsubscribing.
It might take a while before getting this fix.

Taurus code has been changed to reuse DeviceProxy objects to avoid calling DeviceProxy destructor too often. 

Anton could not work on pybind11 rebasing/merging work yet.

### Tango meeting 2020

Please register as soon as possible if you are planning on coming on this site: https://indico.esrf.fr/indico/event/41/

The site has all the info you need to organise your trip - thanks to the organisers Olga + Igor!

**Warning**: St Petersburg is a very popular destination especially with the White Nights festival and Euro 2020 football 
matches this year. You need to book flights + hotels soon if you want to get a seat!

#### Tango Controls Users meeting 2020 contest

Registrants of the meeting have a chance to win a 1-year All products pack personal license from JetBrains.

To be nominated, make a contribution(s) in a period from March, 9th till June, 9th 2020 to any repository in one or both of GitHub organizations: [tango-controls](https://github.com/tango-controls) or [waltz-controls](https://github.com/waltz-controls). Contribution can be everything: from making PR that fixes a typo or PR that performs a full scale refactoring or just creating an issue.

Please create an issue with a link to your contribution in this repository to participate in the contest.

##### How to participate?

1. Register for the [Tango Controls meeting 2020](https://indico.esrf.fr/indico/event/41/registration/signin?returnURL=https%3A%2F%2Findico.esrf.fr%2Findico%2Fevent%2F41%2Fregistration%2Fregister).

2. Contribute to any repository in one or both of GitHub organizations: [tango-controls](https://github.com/tango-controls) or [waltz-controls](https://github.com/waltz-controls):

   * make pull request(s)
   * create an issue(s)
   * perform a code review(s)
   * add a comment(s)

3. [Create an issue](https://github.com/tango-controls/meeting-2020-contest/issues/new) for each contribution in this repository.

##### How to vote?

Thumb up an issue with a contribution that deserves the prize!

##### Reward

Three participants will be awarded a [JetBrains All Products Pack](https://www.jetbrains.com/all/?from=tango-controls).

The jury will choose 1 contribution to be awarded. 
Another 1 contribution will be chosen by the community. Please thumb up an issue with a contribution that deserves the prize!
The last award will be awarded randomly across all the submitted contributions to also encourage small contributions.
 
Anton and Reynald (Igor probably as well?) are already volunteers to be members of the jury. 
More volunteers from the Tango kernel developers are welcome.

**Igor**: The Jury: Igor, Olga, Reynald, Anton. We need to decide on which date the award will be perofrmed. On the eve the Jury will need to gather and pick one contribution.

## High priorities issues

- [cppTango#686](https://github.com/tango-controls/cppTango/issues/686)
- cppTango conda package for cppTango 9.3.3 and 9.3.4.
- JTango fix for heartbeat events

## AOB

### JetBrain licenses

If a Tango kernel developer needs a JetBrain license, please contact Reynald, Andy or Igor.

### Conda packages

Reynald will work on [tango-conda-recipes](https://github.com/tango-controls/tango-conda-recipes) to use Github actions to create conda packages and 
then deploy them easily on the official tango-controls conda channel. The priority for this task was risen. 

### HDB++

**Action - ESRF**: Reynald will send a framadate poll to find a good date for an HDB++ teleconf meeting, since a face to face meeting is discouraged during this period.

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET (Paris time).

The next Tango kernel teleconf meeting will take place in 2 weeks on Thursday 26th March 2020 at 15:00 CET.

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2020/2020-02-27/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - All**: Test [9.3.4-rc4](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc4) release when it will be out.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the 
TangoSourceDistribution repository.

**Action - Soleil**: Implement the fix for events with network aliases.

**Action - S2Innovation?**: Create a page in tango-doc where each institute could list the operating systems where cppTango and PyTango are running in their institutes.
It could probably be interesting to list as well the java versions used for the JTango applications. 
**Piotr will start to send e-mails next week to gather the information from the community. 
It would be good to find a way to keep this information up to date. 
Sending a reminder once a year would be already something useful, maybe around the Tango meeting date?**.

**Action - volunteers**: Review TangoSourceDistribution PRs.

**Action - ESRF?**: Move pytango conda recipes to a new repository in tango-controls Github organization. 
**Done**: https://github.com/tango-controls/pytango-conda-recipes and 
https://github.com/tango-controls/pytango-windows-conda-recipes have been created.

**Action - cppTango developers and volunteers**: Review the TangoTest PRs.**No activity since the last meeting**

**Action - S2Innovation?**: Create an issue in tango-doc (if does not exist yet) to ask for an improvement of the event 
system documentation. **Done. Someone from S2Innovation will work on that, but not before April**

## Summary of remaining actions

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - All**: Test [9.3.4-rc4](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc4) release when it will be out.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the 
TangoSourceDistribution repository.

**Action - Soleil**: Implement the fix for events with network aliases.

**Action - S2Innovation**: Create a page in tango-doc where each institute could list the operating systems where cppTango and PyTango are running in their institutes.
It could probably be interesting to list as well the java versions used for the JTango applications.

**Action - volunteers**: Review TangoSourceDistribution PRs.

**Action - cppTango developers and volunteers**: Review the TangoTest PRs.

**Action - S2Innovation**: Create a new cppTango issue to track the problem mentioned while reviewing [cppTango#593](https://github.com/tango-controls/cppTango/pull/593).
 Issue with missing pipe events when RestartServer is called.
 
 **Action - ESRF**: Reynald will send a framadate poll to find a good date for an HDB++ teleconf meeting, since a face to face meeting is discouraged during this period.
