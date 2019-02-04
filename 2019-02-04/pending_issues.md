
Purpose of this document is to organize the list of topics shared by each institute before the kernel meeting






Critical issues on tango
========================

- Make the new release of Tango 9.3 / PyTango 9.3

- Fix last known bugs in event system (IDL4 compat, DataReady and Pipe
events idl5_ prefix wrongly added)

- Add Changelog.md and improve Release Notes

ALBA:
● change/archive push event performance: could we have a single push_event with 
  - push_event(value, CHANGE|ARCHIVE mask)
  - integrate alba's pull request: [link]
  - with PR then change in core would be less critical

ALBA:
- Not possible to subscribe to events in server initialization phase #7
● Add server_init_hook() method #498
● Device server crashes on Windows when reading attribute in between its two
devices #19
- Tango Monitor problems on server startup #12


Problems
========

- Fix bugs reported by sonarcloud and flag as false positive the false
positive (!)
- Improve the Travis tests

● Not all messages from a DS are logged when launched from Astor #24

ALBA:
 - help needed for packaging Tango / PyTango in the future? 

ALBA:
 - event-subscriber not started despite of context=ALWAYS

PyTango: Study DS problem when using taurus 4 attribute (with serial mode)
● How to reproduce:
● PyTango device server.
● Device creates a taurus device to some remote device and adds a listener.
● Shutdown the device server cannot be killed anymore from Astor

- Units: A string unit property is missing to for standard unit label
 -- Check if already done and document it

Documentation pending
=====================

- improve the Contributions.md file from cppTango to give more details on
how to create a Pull Request.
● add an easy-access link to JTango javadoc in JTango documentation as
well as in the tango-controls documentation.

- Warning about forwarded attributes which are currently not reliable.

ALBA: HDB++ status:

● mysql/mariadb divergence
● lack of collaboration/sharing?
● myIsam/Aria/InnoDB comparison in cpu/disk usage
● comments/results on JSON implementation for arrays
Hint: Try SSD disks

PyTangoArchiving:
 - how to correlate multiple DB's; switch DB based on date

SOLARIS: decentralization of the database 

 - document existing strategies; multiple tango_hosts, several device servers for same database, database replication
 - document proxysql usage from esrf
 
SOLARIS: archiving of huge amount of data, speeding up Tango

 - Define what is a huge amount of data; what are Tango limits
 - Write a HowTo/recipe for high event rate device servers (at alba we reach up to 400/500 events/s)

SOLARIS: data streaming for high speed detectors:

 - Tango is a control framework, very high speed image streaming may be out of its scope
 - But, would be good to document what is the limit
 
SOLARIS:
 - iot direction, mobile applications

ALBA:
 - status of current Web applications: summarize what exists and status
 ● Fandango / PyTangoArchiving / Panic documentation update ;
integration with tango documentation
● Expand on debugging and testing:
● https://tango-controls.readthedocs.io/en/latest/
development/debugging-and-testing/index.html
● Review of simulators documentation and examples
● Tango.js documentation ? Alternatives?
● Doc Tango source package creation. Missing deps. (Debian)
- Tips for setting new conf. for mariadb
● Tango Heart beat
ESRF: ● add an advanced section on how to debug heartbeat pb with wireshark 
● Tango Unitless vs not unit

Enhancement proposals
=====================

SOLARIS:

 - database engine as plugin
 - simplification of C++ API (something like High Level API in PyTango)
 - transport protocols as plugins

● PostgreSQL/TimescaleDB schema?

● Viewer/Extractor for multiple DB's? Correlate different DB's on java viewer or eGiga?


Things not to solve
===================

- Tango library adaptation to work witch C#

