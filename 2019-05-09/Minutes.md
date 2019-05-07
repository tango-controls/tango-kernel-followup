# Tango Kernel Follow-up Meeting - 2019/05/09

Held on 2019/05/09 at 14:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

Participants: 

# Minutes

## cppTango News

cppTango 9.3.3 has been installed on the ESRF accelerator simulators control systems and on the control system being built for the new accelerator.

No big issue reported so far.

Did anyone else test it?

Can we mark it and advertise it as the new stable release?

## Tango Source Distribution

9.3.3 release is being prepared in [TangoDistribution#18](https://github.com/tango-controls/TangoSourceDistribution/pull/18).

Users can test it by using [prepare-9.3.3](https://github.com/tango-controls/TangoSourceDistribution/tree/prepare-9.3.3) branch.

[TangoDistribution#21](https://github.com/tango-controls/TangoSourceDistribution/issues/21) at least must be fixed before making a release.

[TangoDistribution#22](https://github.com/tango-controls/TangoSourceDistribution/issues/22) would have been nice to have but might require too much resources to get a release delivered quickly.

Some cleanup needs to be done in the README, INSTALL, TANGO_CHANGES and similar files.

## ICALEPCS TANGO Workshop

## JTango News

There is still an event reconnection issue on java client side in a specific case: [JTango#71](https://github.com/tango-controls/JTango/issues/71).

## PyTango News

## Waltz News

* Release [v0.7](https://github.com/tango-controls/waltz/releases/tag/v0.7)
* Release [v0.7.1](https://github.com/tango-controls/waltz/releases/tag/v0.7.1)
* Release [v0.7.2](https://github.com/tango-controls/waltz/releases/tag/v0.7.2)


## HDB++

Do we organize an HDB++ meeting this year? When and where?
Or do we go for some more regular teleconf meetings?

## TangoBox status

## Go through main issues and define priorities

## AOB

## Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2018-11-15/Minutes.md#summary-of-remaining-actions)

**Action - All institutes**: Every institute will send the Windows compiler versions they need (if needed) to Reynald.

**Action - Any (Windows) C++ developer willing to help**: Please help us to solve the Windows specific issues. For 
instance, there is a compilation issue on Windows with cppTango #480 (https://github.com/tango-controls/cppTango/pull/480).

**Action - All institutes**: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would 
like to get solved first.

**Action - Anyone willing to help**: Igor is welcoming any additional advice/help anyone could have to help debugging 
the JTango random timeouts issue.

**Action - S2Innovation**: Prepare a new version of the TangoBox where the Tango events are working properly. **WIP**

**Action - ESRF**: Andy will contact tango-project.eu to inform them about tango-controls and to see whether they could 
use tango-controls. **To be done**

**Action - Alba, All institutes**: 
Review [TangoDistribution#8](https://github.com/tango-controls/TangoSourceDistribution/pull/8)

**Action**: Organize an HDB++ meeting in 2019. Maybe dedicate a full day for an HDB++ meeting during the week of the 
next Tango meeting at DESY.

**Action - ESRF, IK**: JTango: clarify actions to be done to fix the event reconnection issues with java clients 
subscribing to events coming from hosts having several network interfaces"

## Summary of remaining actions
