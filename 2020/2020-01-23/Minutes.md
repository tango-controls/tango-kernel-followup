# Tango Kernel Follow-up Meeting - 2020/01/23

Held on 2020/01/23 at 15:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants:  

# Minutes

## Tango Source Distribution

- 9.3.4-rc3 is available.

- Tango Database DS crash [TangoSourceDistribution#61](https://github.com/tango-controls/TangoSourceDistribution/issues/61): 
The problem was due to a bug in libmariadb2. No problem when using libmariadb18 or libmariadb3.

## cppTango News

### Recent PR merged
Several PRs have been merged since the last meeting.
Here is a list of improvements and bug fixes:
- Require C++ 11 and CMake 3.7 [cppTango#653](https://github.com/tango-controls/cppTango/pull/653)
- Reset Database and DS for each test [cppTango#640](https://github.com/tango-controls/cppTango/pull/640)
- Only install PTHREAD_WIN_FILES if it is enabled [cppTango#644](https://github.com/tango-controls/cppTango/pull/644)
- Fix snprintf detection [cppTango#650](https://github.com/tango-controls/cppTango/pull/650)
- Add testing with Ubuntu Bionic Beaver [cppTango#652](https://github.com/tango-controls/cppTango/pull/652)

### Ongoing tests

Michal has been working on [cppTango#511](https://github.com/tango-controls/cppTango/issues/511).
He proposed [cppTango#641](https://github.com/tango-controls/cppTango/pull/641) to fix the issue.
The patch is currently under test at the ESRF. No crash so far since 2 days.
The device server under test used to crash several times a day before this patch.
Elettra will test the patch too.

### Ongoing developments


### Boost libraries in cppTango
Question raised in [cppTango#648](https://github.com/tango-controls/cppTango/issues/648): Possibility to use boost libraries?

Please do not hesitate to share your opinion and experience on [cppTango#648](https://github.com/tango-controls/cppTango/issues/648) issue.

## JTango News

Gwenaëlle worked on improving the events system in JTango (similar work as what was done in cppTango 9.3).
Some tests have been done at the ESRF. Some issues have been reported and will be fixed.

## PyTango News

## High priorities issues

## AOB

### Tango meetings in Russia
### Conda packages
### TangoTest improvements 
https://github.com/tango-controls/TangoTest/issues

### Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET (Paris time).

The next Tango kernel teleconf meeting will take place on Thursday 13th February 2020 at 15:00 CET.


## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2020-01-09/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would
like to get solved first.

**Action - All**: Please have a look at the stalled PR, comment and update the status if there are some news.

**Action - All**: Please review the remaining actions defined in the previous meeting and update their status in these minutes.
If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

**Action - PR developers**: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts.
Please rebase and solve conflicts if needed to ease the review process.

**Action - Thomas Braun**: Test 9.3.4-rc2 packages from Ping Frédéric Picca, provide feedback, ask to create new packages 
for rc4 (rc3 plus new cppTango plus X).

**Action - All**: Test [9.3.4-rc3](https://github.com/tango-controls/TangoSourceDistribution/releases/tag/9.3.4-rc3) release.

**Action - Max IV**: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the 
TangoSourceDistribution repository.

**Action - S2Innovation**: Piotr said he will take care of the documentation issues reported while preparing this 9.3.4 
Tango source distribution release. 
Piotr will also update the Tango documentation to add links to rpm files created/used by Max IV.

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could
use tango-controls.

**Action - Soleil**: Implement the fix for events with network aliases.

**Action - Elettra**: Tests on PR [cppTango#641](https://github.com/tango-controls/cppTango/pull/641) are welcome.

**Action - Nexeya**: Review [cppTango#642](https://github.com/tango-controls/cppTango/pull/642) and 
[cppTango#644](https://github.com/tango-controls/cppTango/pull/644).

**Action - All**: Agree on where to create a wiki page to list the OS/Compilers used to run Tango in the different institutes.

## Summary of remaining actions