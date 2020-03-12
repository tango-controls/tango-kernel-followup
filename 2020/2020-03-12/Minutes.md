# Tango Kernel Follow-up Meeting - 2020/03/12

Held on 2020/03/12 at 15:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants:  

# Minutes

## Tango Source Distribution

[#69](https://github.com/tango-controls/TangoSourceDistribution/pull/69) (check mariadb version) has been merged.

Simply need to update cppTango Changelog, tag cppTango 9.3.4-rc4 and to update TangoSourceDistribution release notes.

## cppTango News

### Recent PR merged
Several PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:
- appveyor.yml: Add inline deployment on tag push ([#602](https://github.com/tango-controls/cppTango/issues/602), [#616](https://github.com/tango-controls/cppTango/pull/616), [#690](https://github.com/tango-controls/cppTango/pull/690))
- CMakeLists.txt: Add option to disable building the test suite ([#668](https://github.com/tango-controls/cppTango/pull/668))
- Fix omniidl error checks ([#687](https://github.com/tango-controls/cppTango/pull/687))
- Bump release number ([#593](https://github.com/tango-controls/cppTango/pull/593))

### New issues
The following issues and pull requests have been created since the last teleconf meeting and are not yet solved:
- API_ZmqFailed exception thrown in ZmqEventSupplier::push_heartbeat_event leads to program termination ([#691](https://github.com/tango-controls/cppTango/issues/691))

## JTango News

## PyTango News

### Tango meeting 2020

Please register as soon as possible if you are planning on coming on this site: https://indico.esrf.fr/indico/event/41/

The site has all the info you need to organise your trip - thanks to the organisers Olga + Igor!

**Warning**: St Petersburg is a very popular destination especially with the White Nights festival and Euro 2020 football 
matches this year. You need to book flights + hotels soon if you want to get a seat!

#### Tango Controls Users meeting 2020 contest

Registrants of the meeting have a chance to win a 1-year All products pack personal license from JetBrains.

To be nominated, make a contribution(s) in a period from March, 9th till June, 9th 2020 to any repository in one or both of GitHub organizations: [tango-controls](https://github.com/tango-controls) or [waltz-controls](https://github.com/waltz-controls). Contribution can be everything: from making PR that fixes a typo or PR that performs a full scale refactoring or just creating an issue.

Please create an issue with a link to your contribution in this repository to participate in the contest.

The jury will choose 2 contributions to be awarded. Another 1 contribution will be chosen by the community. Please thumb up an issue with a contribution that deserves the prize!

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

## High priorities issues

## AOB

### Conda packages


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

**Action - volunteers**: Review TangoSourceDistribution PRs.

**Action - ESRF?**: Move pytango conda recipes to a new repository in tango-controls Github organization.

**Action - cppTango developers and volunteers**: Review the TangoTest PRs.

**Action - S2Innovation?**: Create an issue in tango-doc (if does not exist yet) to ask for an improvement of the event 
system documentation.

## Summary of remaining actions

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.
