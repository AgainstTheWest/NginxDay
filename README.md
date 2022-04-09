# NginxDay
Nginx 18.1 04/09/22 zero-day repo

# Context
We had been given this exploit from our sister group, BrazenEagle, who had been developing is for some weeks. Or atleast since Spring4Shell came out.
We are still in the early stages of usage and understanding it, as BE are working on another vendor vulnerabiliy.

Regarding the finite details about it, we recommend you check out this tweet:
https://twitter.com/Gi7w0rm/status/1512789855197093891

GitWorm was allowed to share that information with permission from our DMs.

We were initally confused, as LDAP doesn't interact much with Nginx, however, there is an ldap-auth daemon used alongside Nginx, which allows for this to be used.
It primarily is used to gain access to private Github, Bitbucket, Jekins & Gitlab instances. Further testing is required in due time.

### Update 1: As some further analysis is ongoing, the module relating to the LDAP-auth daemon within nginx is affected greatly. ;)
Anything that involves LDAP optional logins works as well. This includes Atlassian accounts. Just working out if we can bypass some common WAFs. Default nginx configs seem to be the vulnerable type, or common configs.

We highly recommend disabling the ``ldapDaemon.enabled`` property. If you plan on setting it up, be sure to change the ``ldapDaemon.ldapConfig`` properties flag with the correct information and don't leave it on default. This can be changed until Nginx (fucking) respond to their emails and DMs.









## This README file will be updated as more information regarding this vuln comes to light. 
