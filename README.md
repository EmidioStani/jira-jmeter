jira-jmeter
=================

The original files are available on Atlassian [web site](https://confluence.atlassian.com/display/JIRA/Performance+Testing+Scripts).

I updated the script, based on version [5.1.1](http://maven.atlassian.com/public/com/atlassian/performance/jira/performance-test/), by fixing some issue and adding new features.

The script needs some fixes:

1. it doesn't use the varialbe MaxProject, so I removed it

Therefore after you download the script (with the resources) just remember to adapt the Crowd configuration (parameter -Jcrowd.host) and that the operation Create User from Crowd expect to have Crowd under the same ip address of Confluence (you can of course change it).

The script has been executed on Jira 5.1.6 with Jmeter 2.7