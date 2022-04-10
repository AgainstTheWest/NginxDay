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

### Update 1: 
As some further analysis is ongoing, the module relating to the LDAP-auth daemon within nginx is affected greatly. ;)
Anything that involves LDAP optional logins works as well. This includes Atlassian accounts. Just working out if we can bypass some common WAFs. Default nginx configs seem to be the vulnerable type, or common configs.

We highly recommend disabling the ``ldapDaemon.enabled`` property. If you plan on setting it up, be sure to change the ``ldapDaemon.ldapConfig`` properties flag with the correct information and don't leave it on default. This can be changed until Nginx (fucking) respond to their emails and DMs.

### Update 2:
Been talking to some infosec people about this, some mixed responses. Some are saying it's a problem with LDAP itself and not Nginx, while ``ldapDaemon`` isn't always used. The exact quote is "CI/CD pipeline hardens the instance, one of the steps is to completely strip out the LDAP module.". This is partially correct. In fact, it is an option when compiling nginx. However, it could be a problem with LDAP itself.

The issue with this, is that it only works with nginx instance using LDAP, such as any login portal that supplies that authentication method. 

Further analysis and testing is required. Looks to only be affecting this version. If it affects updated versions of the LDAP protocol, then we'll see what comes of that.

### Update 3:
I (as I'm still in ATW, but I'm just the only one online) have forwarded our own questions, community concerns, further testing questions to BrazenEagle via email. They have yet to respond, as they are US-based. Hopefully, they can provide some further answers. Shouldn't leak it, but their main contact email is brazeneagle@riseup.net (duh!). 

While I'm still skeptical on the workings of this issue, it would explain the companies that were breached in under an hour during testing with BrazenEagle. They stated that they had passed this exploit to us as they were "working on more luctitive exploits". What that means, I'm not so sure.

Some few individuals were (clearly) told about this being in the works some months ago via Telegram chats, which maybe perhaps some Twitter infosec people were talking about it and ATW.


## This README file will be updated as more information regarding this vuln comes to light. 
