![Logo](https://i.ibb.co/k5jFkC0/nd22.png)


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

### Update 4:

Regarding what people have been suggesting on twitter and on the issues page about this only being a LDAP or Bitnami issue, the problem with this is, during testing phases, it's only worked on Nginx, not on Apache or other web servers. Also, Nginx have still not replied. DMs or E-mail. We've emailed some companies that are affected that we've not breached (since that's heavily against our ideals) for support on the matter regarding security around this exploit.


### Update 5:
So, we've been followed by an employee of Nginx on Twitter. Threw our a DM asking about the situation, no responce yet.
We've been working on another exploit for MongoDB and another database management framework. Looking to have the PoC out in a week's time. Video as well. Will be working on it with @Gi7w0rm on Twitter.

### Update 6:
:O We got a DM from Nginx on twitter regarding the issue:
![Twitter DM with Nginx](https://img001.prntscr.com/file/img001/KaV8MJrDTuu4LBHPEC03CA.png)


### Update 7:

https://twitter.com/nginx/status/1513670892987031552


## Update 8:

As Nginx have now released a blog post about the public releases of information, we've emailed them with a description, some familiarities of the issue that they highlighted over and assets affected. However, people are quick to jump on the "This is fake" or "This isn't anything" bandwagon. As we got no answer to if there is any bounty offered by Nginx for the findings, we've not shared any deeper information about this. If there is no bounty or even reward, we've looked at the other option that would be to sell the exploit on either breached.co, exploit.in or other sites. (We've been offered about 200K in XMR for the exploit).

If you're thinking that we're "Only interested in money", yes, what do you expect? We're a threat group, lol

## This README file will be updated as more information regarding this vuln comes to light. 

# Contact & other
Our Email: AgainstTheWest@riseup.net
Twitter: https://twitter.com/_Blue_Hornet

Donate XMR: 85gUB5bvFwR5JVXig3QgPuRT3k83igXGy8Lk7dRJud5aepkzkSLqFv3CPFbEDPEapEHvNY5xr2Uhdj8YLbcJyKPMB3ijVXW
