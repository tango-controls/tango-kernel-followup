
Purpose of this document is to organize the list of topics shared by each institute before the kernel meeting

Also on: https://hackmd.io/JdQKNVISTBimKtcade7TIw





Critical issues on tango
========================

- Make the new release of Tango 9.3 / PyTango 9.3

- Fix last known bugs in event system (IDL4 compat, DataReady and Pipe
events idl5_ prefix wrongly added)

- Add Changelog.md and improve Release Notes

ALBA:
- change/archive push event performance: could we have a single push_event with 
  - push_event(value, CHANGE|ARCHIVE mask)
  - integrate alba's pull request: [link]
  - with PR then change in core would be less critical

ALBA:
- Not possible to subscribe to events in server initialization phase #7
- Add server_init_hook() method #498
- Device server crashes on Windows when reading attribute in between its two
devices #19
- Tango Monitor problems on server startup #12

Python 2 vs Python 3: DevString with bytes -
 - https://github.com/tango-controls/pytango/issues/251 

Problems
========

- Fix bugs reported by sonarcloud and flag as false positive the false
positive (!)
- Improve the Travis tests

SKA:
 - PyTango, get unit tests passing on Travis CI again
 - testing client and server across different Python versions (e.g. 2.7
client with 3.7 server).

Forward attributes issues:
 - Add to docs Warning about forwarded attributes which are currently not reliable.
 
ALBA:
 - Not all messages from a DS are logged when launched from Astor #24

ALBA:
 - help needed for packaging Tango / PyTango in the future? 

ALBA:
 - event-subscriber not started despite of context=ALWAYS

HDB++:
 - data retrieval problems: Hint: Try SSD disks


PyTango: Study DS problem when using taurus 4 attribute (with serial mode)
 - How to reproduce:
 - PyTango device server.
 - Device creates a taurus device to some remote device and adds a listener.
 - Shutdown the device server cannot be killed anymore from Astor

 - Units: A string unit property is missing to for standard unit label
  - Tango Unitless vs not unit
  - Check if already done and document it

Documentation pending
=====================

 - improve the Contributions.md file from cppTango to give more details on
how to create a Pull Request.

- add an easy-access link to JTango javadoc in JTango documentation as
well as in the tango-controls documentation.

ALBA: HDB++ status:

 - mysql/mariadb divergence
 - myIsam/Aria/InnoDB comparison in cpu/disk usage
 - comments/results on JSON implementation for arrays

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
 - iot direction, mobile applications, how are we related? add a note to the main website
 
SKA:
 - get a better understanding of PyTango architecture

ALBA:
 - status of current Web applications: summarize what exists and status
 - Fandango / PyTangoArchiving / Panic documentation update ;
integration with tango documentation
 - Expand on debugging and testing:
 - https://tango-controls.readthedocs.io/en/latest/development/debugging-and-testing/index.html
 - Review of simulators documentation and examples (tango-simlib / simulatords)
 - Doc Tango source package creation. Missing deps. (Debian)
 
 - Tango Heart beat: how it works??

ESRF: 
 - add an advanced section on how to debug heartbeat pb with wireshark 

Enhancement proposals
=====================

Thomas Braun: 
 - using namespace: https://github.com/tango-controls/cppTango/issues/206 
 - Database with SQLite: https://github.com/ALBA-Synchrotron/pydatabaseds
 
MAX IV:
- CORBA alternative
- Run Tango on k8s (related to CORBA as well)

SKA:
Debian science gitlab pipeline?
https://salsa.debian.org/science-team/pytango 

SOLARIS:

 - database engine as plugin
 - simplification of C++ API (something like High Level API in PyTango)
 - transport protocols as plugins

ALBA:

- PostgreSQL/TimescaleDB schema?
 - Viewer/Extractor for multiple DB's? Correlate different DB's on java viewer or eGiga?

SKA: 

 - ability to set a different log level for each log target. This is
part of the SKA design guidelines. We need the same device to log
to 3 different targets, each with an independently configured log
level.
- support for vector of Enum
- support for complex data type (e.g. re,im)
- support for alarm event
- support for hysteresis in TANGO attribute alarms
- profiling support, e.g. device server collects statistics about connections, events/s, commands, attribute reads....
- simulation support (device mockup)


Others:

- Tango library adaptation to work witch C#

