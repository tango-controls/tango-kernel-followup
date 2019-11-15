# Tango Kernel Follow-up Meeting - 2019/11/15

To be held on 2019/11/15 at 15:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

# Agenda
 1. Tango Source Distribution News
 2. cppTango News
    - Require newer C++ compilers
      In the cppTango project we would like to move to C++11/C++14.
      For this we would require newer minimum compiler versions.
      It would be interesting to hear which old OS versions still
      need to be supported. 
    - Require newer cmake version. As we move to more C++11 features, it
      would avoid a lot of additional work if we could use a newer cmake
      version which has the required checks builtin. From reading [[1]]
      it seems 3.7 would be good already, this was shipped with debian stretch (oldstable). 
      Older distros can just download/compile a newer cmake version version as we do now for debian wheezy [[2]]. 
    - cppTango next release number (9.4 or 10.0?) [#593](https://github.com/tango-controls/cppTango/pull/593)
    - Question raised in [#555](https://github.com/tango-controls/cppTango/pull/555) (Fix crash during alarm state evaluation if attribute value is not set)
    - Questions raised in [#504](https://github.com/tango-controls/cppTango/pull/504) (PR to fix #368): Pushing events for State and Status with quality factor and timestamp.
    - [#620](https://github.com/tango-controls/cppTango/issues/620) and [#540](https://github.com/tango-controls/cppTango/issues/540) follow-up?
 3. JTango News
 4. PyTango News
 5. High priority issues
 6. AOB
 7. Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2019-05-28/Minutes.md#summary-of-remaining-actions)

[1]: https://cmake.org/cmake/help/v3.7/manual/cmake-compile-features.7.html#manual:cmake-compile-features(7)
[2]: https://github.com/tango-controls/cppTango/blob/2ed9451cda9a89bd59a7c5e99888f6fd50a5812a/.travis/debian7/Dockerfile#L27
