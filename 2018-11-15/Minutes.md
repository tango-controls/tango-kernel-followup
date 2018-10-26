# Tango Kernel Follow-up Meeting - 2018/11/15

Held on 2018/11/15 at 14:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants: Reynald Bourtembourg, Andrew Goetz (ESRF)



# Minutes

## Next Tango kernel and documentation meeting (where and when?) 
## cppTango News (cppTango 9.3.2, ...)
## Windows support (VS2017support, ...)
## Tango Source Distribution
## JTango News
## PyTango News
## Waltz News
## TangoBox status
## Go through main issues and define priorities
## AOB
## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2018-09-14/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Every institute will send the Windows compiler versions they need (if needed) to Reynald.

**Action - Any (Windows) C++ developer willing to help**: Please help us to solve the Windows specific issues. For instance, there is a compilation issue on Windows with cppTango #480 (https://github.com/tango-controls/cppTango/pull/480).

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would like to get solved first.

**Action - Igor**: Igor volunteered to spend some hours from his contract on the Tango Source Distribution.

**Action - ESRF**: ESRF will create something like a Doodle to find the best dates for the next Tango kernel and documentation meeting.

**Action - Igor?**: A PR with the backport of JTango fix for the reconnection bug when there are several network interfaces will have to be created especially for tango-9-lts, adapting the original PR to avoid all the deprecations it introduced originally.

**Action - Anyone willing to help**: Igor is welcoming any additional advice/help anyone could have to help debugging the JTango random timeouts issue.

**Action - Igor**: Igor will contact JetBrains to renew the JetBrains licenses used by the Tango kernel developers.

**Action - S2Innovation**: Prepare a new version of the TangoBox where the Tango events are working properly.

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could use tango-controls.

## Summary of remaining actions

