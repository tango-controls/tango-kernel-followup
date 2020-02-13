# Tango Kernel Follow-up Meeting - 2020/02/13

To be held on 2020/02/13 at 15:00 CET on https://esrf.vidyocloud.com/join/UVrb371ZVe

# Agenda
 1. Status of [Actions defined in the previous meetings](https://github.com/tango-controls/tango-kernel-followup/blob/master/2020/2020-01-23/Minutes.md#summary-of-remaining-actions)
 2. Tango Source Distribution News
 3. cppTango News
    - Discussion on how to fix [cppTango#401](https://github.com/tango-controls/cppTango/issues/401). 
    In particular, what should we do if a user wants to change the max value attribute property of a memorized attribute and when the new max value is below the current attribute set point (which is memorized)?
 4. JTango News
 5. PyTango News
    - Issue [#292](https://github.com/tango-controls/pytango/issues/292) related to `__del__` and `DeviceProxy` destructor deadlock:  making good progress.
    - A new release should be made soon - there are some useful additions.
 6. High priority issues
 7. AOB
    - Tango meetings in Russia
    - Conda packages
      - update cppTango from 9.3.2 to 9.3.3 (also used for PyTango CI tests).  Need to move/fork from https://gitlab.com/tiagocoutinho/tango-conda-recipes/ to https://gitlab.com/tango-controls.
      - Also move [pytango-conda-recipes](https://gitlab.com/tiagocoutinho/pytango-conda-recipes) and [pytango-windows-conda-recipes](https://gitlab.com/tiagocoutinho/pytango-windows-conda-recipes)
      - maintainers?
    - TangoTest improvements (https://github.com/tango-controls/TangoTest/issues)
