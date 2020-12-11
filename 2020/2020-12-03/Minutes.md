# Tango Kernel Follow-up Meeting - 2020/12/03

Held on 2020/12/03 at 14:00 CET on Zoom.

# Minutes

## Support for device level dynamic attributes (#814)

**Participants**: Reynald Bourtembourg, Andrew Goetz, Emmanuel Taurel (ESRF), Henrik Enquist, Vincent Hardion (MaxIV), 
Michal Liszcz (S2Innovation), Lorenzo Pivetta (ELETTRA), Sergi Rubio (ALBA) 

Henrik Enquist presented the details of the issue he would like to solve ([cpptango#814](https://github.com/tango-controls/cpptango/issues/814)) 
and the results of his first investigations.
The participants agreed on the fact that the current implementation is not consistent between dynamic commands and 
dynamic attributes and on the fact that consistency is desirable.  
They also agreed on the fact that the consistency is also desirable between a single device exported in a Device Server instance 
and an equivalent device with the same properties exported in a device server exporting several devices.  
With the current implementation, some dynamic attributes can be created in the first case but sometimes not in the latter.

Henrik Enquist will propose a PR to remove the current limitations on the dynamic attributes.

## Travis-ci.org shutdown & migration to travis-ci.com (#812)

**Participants**:  Reynald Bourtembourg (ESRF), Michal Liszcz (S2Innovation), Vincent Hardion (MaxIV), Carlos Pascual (ALBA), Lorenzo Pivetta (ELETTRA)

See https://github.com/tango-controls/cppTango/issues/812 for context. In short travis-ci.org is turning into travis-ci.com offering limited free service, starting 1st January 2021. Projects using travis are on critical path.

The main considerations re GH vs GL are

1. **Freedom** GL is Free Software while GH is not. This should be important for a FOSS-based collaboration such as Tango.
2. **Homogenizing enviroments:** many institutes in the Tango collaboration already run their own GL self-hosted instances. Moving to GL may facilitate community learning and cooperation.
3. **CI improvement:** Continuous Integration in GL is very good and well-tested.
4. **Packaging and dockerization:** gitlab-ci can be used for collaborative packaging. ALBA and SKA already do.
5. **Mail interface:** GL supports an email-based helpdesk (e.g. users could email to incoming+tango-controls/tango@incoming.gitlab.com and the emails are automatically converted to issues). This lowers the barrier for reporting issues and enables some automatizations.
6. **Avoid vendor lock-in:** currently the company behind GL has much better reputation than the one owning GH with respect to Free Software. Moreover, even in the case we need to move away from GL, and forking GL seems barely feasible (even if possible because of "1!), self-hosting looks likely a viable solution.
7. **Unlimited private projects:** GL now allows hosting unlimited private projects for free. Not that relevant for a Free Software community like Tango, but still it can be interesting for some starting projects, or for some proprietary projects based on tango.

An additional consideration on the big picture

9. If a FLOSS hosting software is a crucial point, then we can also not use the gitlab Gold/Ultimate variants as these are closed-source software, see https://about.gitlab.com/install/ce-or-ee/. Experience/feedback is gitlab is "cool", e.g. has concrete advantages, starting with premium.
10. GH is the de-facto reference for any community based project

**Options**

a. dismiss travis and move to github actions
- keep tango-controls on github
- github actions have been tested for some projects in tango, but still early stage
- not much knowledge of GH actions within the Tango community
- at this time of writing github actions come for free
- possibly, runners can be self hosted

b. keep tango controls on github and move CI to gitlab
- it is feasible setting un CI on gitlab keeping the source on github, but requires a premium account and does not integrate well with PR, see https://docs.gitlab.com/ee/ci/ci_cd_for_external_repos/. No detailed info per job.

c. move tango-controls to gitlab
- moving from GH to GL seems straightforward, see https://gitlab.com/tango-controls/test_gh_import/cppTango and https://gitlab.com/-/snippets/2046070
- appveyor supports gitlab, see https://gitlab.com/bourtemb/cppTango/-/pipelines as a test output, so it seems feasible using appveyor as now, before using windows runners
- GL grant free of charge licences are either Gold (Gitlab hosted) or Ultimate (self hosted). Gold option limited to 50000 CI minutes/month.
- possibly, just runners can be self-hosted, if CI minutes shortage (in fact, not just a mere possibility. Concrete options are self-host or buy additional minutes from day 1)
- GH repos can stay in place during transition time as a synchronized mirror of GL
- GL uses openID authentication, thus users who already have a GH account don't even need to create a new one on GL (but may want to)
- need to understand better whether self-hosting is preferable/required and viable (who? where?)


   
