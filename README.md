jira-jmeter
=================

The original files are available on Atlassian [web site](https://confluence.atlassian.com/display/JIRA/Performance+Testing+Scripts).

I updated the script, based on version [5.1.1](http://maven.atlassian.com/public/com/atlassian/performance/jira/performance-test/), by fixing some issue and adding new features.

The script needs some fixes:

1. it doesn't use the varialbe MaxProject, so I removed it
2. the regular expression for project id, priority, issue id and workflow have been changed
3. rarely when creating an issue, Jira doesn't generate the list of projects for the issue, so in case the regular expression fails tol extract the projects, I go on the project list page and I take one randomly
4. the default group is jira-users for all types of users and it can be passed as parameter
5. the response assertion for View Project has been changed


Further I improved the script giving the possibility:

1. to create users from Crowd, using a new command line parameter -Jenable.sso=true, which is false by default
2. to use https in case Confluence is setup with https instead of http, using a new command like parameter -Jconfluence.protocol=https, which is http by default

Therefore after you download the script (with the resources) just remember to adapt the Crowd configuration (parameter -Jcrowd.host) and that the operation Create User from Crowd expect to have Crowd under the same ip address of Confluence (you can of course change it).

The script has been executed on Jira 5.1.6 with Jmeter 2.7 and on Jira 5.2.8/11 with Jmeter 2.9

Setup:

```jmeter.bat -t ..\..\jira-jmeter-master\jmeter-test-setup.jmx -Jadmin.user=ADMINUSER -Jadmin.pass=ADMINPASSWORD```
```-Jjira.host=SERVERNAME -Jjira.port=443 -Jjira.context=/jira -Jenable.sso=true -Jjira.protocol=https```

Execution:

```jmeter.bat -t ..\..\jira-jmeter-master\jmeter-test-fixedload.jmx  -Jadmin.user=ADMINUSER -Jadmin.pass=ADMINPASSWORD```
```-Jjira.host=SERVERNAME -Jjira.port=443 -Jjira.context=/jira -Jjira.protocol=https```

Deletion:

```jmeter.bat -t ..\..\jira-jmeter-master\jmeter-test-setup.jmx -Jadmin.user=ADMINUSER -Jadmin.pass=ADMINPASSWORD```
```-Jjira.host=SERVERNAME -Jjira.port=443 -Jjira.context=/jira -Jremove.data=true -Jjira.protocol=https```
