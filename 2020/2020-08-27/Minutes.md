Tango Kernel Follow-up Meeting - 2020/08/27

Held on 2020/08/27 at 15:00 CEST on Zoom.

Participants: Andy Gotz (ESRF - minutes), Anton Joubert (SKA-ZA), Michal Liszcz, Wojciech Kitka, Piotr Gregor (S2Innovation), Thomas Braun (byte physics), Nick Rees (SKAO)
Minutes
Status of Actions defined in the previous meetings

Action - All institutes: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would like to get solved first.

Action - Kernel developers: Look at https://github.com/pulls/review-requested and review/merge pending PRs

Action - All: Please have a look at the stalled PR, comment and update the status if there are some news.

Action - All: Please review the remaining actions defined in the previous meeting and update their status in these minutes. If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

Action - PR developers: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts. Please rebase and solve conflicts if needed to ease the review process.

Action - All: Test 9.3.4-rc6 release. Thomas is currently testing the 9.3.4-rc6 latest experimental Debian package and will check whether the issue related to the DB update is still present.

Action - Max IV: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the TangoSourceDistribution repository.

Action - Alba: Add content to known issues section of the documentation to share some known work-around tricks.

Action - Soleil: Fix last issues with events in JTango and release a new JTango version which will be used in the next Tango Source Distribution release. JTango 9.6.1 has been released on 16/07/2020. The event issues should be fixed in this version. Some problems seem to remain according to Zibi: See https://github.com/tango-controls/JTango/issues/90

Action - ESRF: Prepare cpptango 9.4.x conda package based on tango-9-lts branch. Some conda cpptango and tango-test conda packages using cppTango tango-9-lts branch have been generated and can be downloaded on https://github.com/tango-controls/tango-conda-recipes/actions/runs/164651901

Action - ESRF (Andy): Create an issue (in TangoTickets) to transmit a more meaningful error message when Corba Transient Timeout exception are received.
Tango Kernel training

Action - ESRF: organise a Tango kernel training

Tango Kernel Training

The Tango Kernel training was discussed following the request by Nick Rees (SKA) on tango-controls #kernel slack channel.

Everyone agreed with the approach to share the training between the different C++ Kernel experts - Reynald, Emmanuel, Mihal and Thomas.
The format will be a series of short webinars (1 to 2 hours) which will be recorded. 
The topics of the webinars will be decided based on the interests experessed by the audience. 
The first topic will be an introduction to the kernel code, how it is organised and how to set it up to contribute.

The following date was agreed on for the first training - 26 October 2020 in the morning (in Europe) so that time zones in Asia and Australia can participate.

The frequency of the webinars should be one webinar per month.

PRs have been merged since the last meeting. Here is a list of improvements and bug fixes:
tango-9-lts (future 9.4)

    cppTango#698 is waiting for feedback from RB, ML said it can be backported and proposed that it be done on a backport branch

9.3 backports



New issues

The following new issues have been created in cppTango since the previous Tango Kernel teleconf meeting:

    Problems when cross compiling for ARM (cppTango#740)
    Disallow for event subscription and unsubscription using different device proxies (cppTango#747 According to Michal, this one is not difficult to solve but will require cppTango#746 to be merged first.
    Add Tango::Group::set_source(Tango::DevSource ) method (cppTango#749)
    DeviceProxy::subscribe_event(Tango::INTERFACE_CHANGE_EVENT,cb_ptr,true) throwing exception when target device server is not running (cppTango#750)

Recent developments

Thomas tested 9.3.4-RC6 on Debian and found that the database was missing.


JTango News

The question was raised if the Jtango#90 issue has been solved (problem with events and heartbeats). If not it should be reopened.

PyTango News

Wojciech Kitka is fighting with the Windows build issue. He is close to solving the problem and thinks he can solve the problem with an extra 2 weeks of effort. 
In case this is not the case it will be discussed at a future meeting if it needs to bdropped or not. 

Tango Source Distribution

Thomas worked on TangoSourceDistribution#85 (merged)) to avoid checking database server process presence when executing "tango start" script. This pull request solved TangoSourceDistribution#84 Thomas is currently testing 9.3.4-rc6 experimental Debian package and preparing 9.3.4-rc7.
Conda packages

cpptango 9.4 beta version conda package ((tango-conda-recipes#7). Reynald has done some work on that and managed to generate packages using Github workflow. Please refer to https://github.com/tango-controls/tango-conda-recipes/pull/8 github workflow artifacts. Anton would like to get this conda package on a conda channel. He proposed to Reynald to upload it on his personal conda channel (Reyn4ld). It has to be noted that this package is built based on tango-9-lts cppTango branch which is the cppTango 9.4 development branch (so a moving target), so if this package is built at different times, it might use different versions of the tango-9-lts cppTango branch.

No new high priority issue reported since the last meeting. Here are the high priority issues defined during the previous meeting:

On PyTango, the priority is on the Windows build (and tests passing on Windows).

The others priorities are:

    Conda package with support for Python3.8 pytango#346)
    Safe interworking between read_attribute() and push_event() (cppTango#698)
    Event subscription lost when destroying different DeviceProxy instance (pytango#372)
    Exception on unsubscription when a client has two proxies for the same attribute (cppTango#353)

AOB

This was not mentioned during the teleconf meeting but a new TangoTickets issue has been created:

    Concurrently executing a command and pushing event leads to dead lock TangoTickets#39

Next teleconf meeting

Tango kernel teleconf meetings take place on the 2nd and 4th Thursday of each month, at 15:00 CET or CEST (Paris time).

The next Tango kernel Teleconf meeting will take place on Thursday 10th September 2020 at 15:00 CEST.
Summary of remaining actions

Action - All institutes: Please vote (+1 comment in the issue, or e-mail) for the most critical issues you would like to get solved first.

Action - Kernel developers: Look at https://github.com/pulls/review-requested and review/merge pending PRs

Action - All: Please have a look at the stalled PR, comment and update the status if there are some news.

Action - All: Please review the remaining actions defined in the previous meeting and update their status in these minutes. If the action is not solved, please put it in the "Summary of remaining actions" section in these minutes.

Action - PR developers: Please ensure the old opened PRs are still compatible with the latest version of tango-9-lts. Please rebase and solve conflicts if needed to ease the review process.

Action - All: Test 9.3.4-rc6 release.

Action - Max IV: Vincent Hardion will ask his colleagues to create Pull Requests to integrate spec rpms in the TangoSourceDistribution repository.

Action - Alba: Add content to known issues section of the documentation to share some known work-around tricks.

Action - Soleil: Fix last issues with events in JTango and release a new JTango version which will be used in the next Tango Source Distribution release.

Action - ESRF: Prepare cpptango 9.4.x conda package based on tango-9-lts branch and upload it to Reyn4ld conda channel to ease testing by Anton.

Action - ESRF (Andy): Create an issue (in TangoTickets) to transmit a more meaningful error message when Corba Transient Timeout exception are received.
