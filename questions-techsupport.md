## Howdy!

Welcome, we're so excited to have you here! The purpose of this gist is to get to know you a bit better and understand your communication style when talking with our users. Please read through and let us know at any point if you have any questions!

## Answer the test tickets
Below you'll find several faux support tickets. Names and identifying information have been changed, but otherwise these support requests are pretty faithful. We've also written some information that should give you an idea of how we go about answering the questions we get. 

## GitHub support tenets: a tl;dr

### Logic + empathy
It's a satisfying balance to bring both analytical skills to a problem, but also remember to respond to a user with care.

### Transparency + honesty
We put effort into writing up [post-mortem blog posts about What Went Wrong](https://github.com/blog/1397-recent-code-search-outages). The balance here is to show enough transparency so users feel respected, but in the case where things are horribly wrong, not share so much that we overwhelm them. 

[Here's an example of a support request](https://gist.github.com/3e89df1f7c0e7d6d5737). It may be easier to say something vague and not-technically-untrue like "there was a small problem and we fixed it". It means we don't have to cop to a mistake on our end. Our users are in the tech world, and are used to figuring out problems. We have found we're much better off telling them what's up, and why.

### Surprise + delight
We have an awesome user base, who generally think we're pretty great. We've put a lot of social effort into drinkups, conference talks and blog posts that wow people and create fans of our company and the products we [ship](http://shipitsquirrel.github.io/images/ship%20it%20squirrel.png).

We follow the [Terms of Service](https://help.github.com/articles/github-terms-of-service), and go above and beyond when it's appropriate. We have the ability to refund as much as we want, and to offer coupons as often as we want. We use this judiciously, as you can turn a surprise into disappointment if wielded badly. You can go back to logic+empathy to consider if what you'd like to do will actually delight the user.

Often, our users may just need information quickly and clearly, without being goofy. We have to know how to respond in the way that best matches how the user is feeling.

### GitHub voice

To explain it casually, we try to exude something that sounds like the person:

* is a real human
* is invested in things going well for you (we care)
* is really smart, but kind (not egotistical)
* and maybe kind of funny (good robot test)
* or at least interesting (and also not actually a robot)
* is not businessy
* could be found in a hoodie, blaring music, slouching in a bean bag chair

### Humble brag
Here's what someone wrote about us, in a longer piece about moving their company to GitHub:
>This leads me to the Customer Service itself. The GitHub staff I’ve been in contact with is extremely helpful, efficient, and comprehensive of our specific requirements. Most important: you deal with real people with real names, not with an anonymous service. When a member of the support staff takes your case (which happens in minutes, even for us Europeans), you get in touch with this person each time you interact on the case. And their CRM tools seem good enough so that your customer history is quickly available to all the support staff. I must say that I didn’t expect such a good customer service from a company with a reputation of automating everything they can, but they really take customer relationship seriously.

### An FYI on how we work
Most of the support team is remote, so we use a group chat room and a support app to work together. We also use GitHub -- it's where the code is stored, where we log bugs, and where we collaborate on new ideas. We don't tend to email or call each other, though we'll videochat every once in a while to catch up. Mostly we hang out in the support chat room to communicate.

***********************************

## Support tickets 

### Ticket #1: Rejected pull request from fork 

>To start, I have to say I LOVE GITHUB. You guys rock. I was at your 4th birthday party, thanks for the cupcake and booze!

>Anyway, here's my problem. I sent a pull request to technoweenie, and he rejected it because my master branch is out of sync. What can I do to fix this?

>Help me supportocat, you're my only hope!

>/.Steve

Hint: You'll want to address their question, and you could add an explanation of topic branches as a better workflow.

### Ticket #1 response:

Hi Steve,

Thank you so much for your kind words. Your happiness is our biggest priority and I am so glad that you love our product! 

I'm sorry that you're having a problem with a rejected pull request. As you said, it was rejected because your master branch is out of sync.

An out of sync master can happen when the remote repo has received a forced push (git push --force) which rewrite the history.

If you have done commits of your own on master:

make a branch (to remember the current master state)
git branch old_master

make sure you don't have any private file you need to save.

That would be:

git fetch origin
git reset --hard origin/master
git clean -f -d

(you can preview the last cleaning steap with a '-n' option: git clean -n -f -d)

Note that git fetch origin master && git merge origin master could be a git pull origin master: the interest of keeping the two steps separated is to look at the difference between master and origin/master before the merge.
If you don't make that diff, then a git pull is simpler.

The main idea is to never ever commit to the master branch in your fork, and only use it as a reference for the upstream changes. all changes are made in topic branches, 
then you're rebasing those onto the master branch, and then you're creating pull requests. if you are working on multiple issues, simply create multiple topic branches 
off the master branch.

Topic branches are typically lightweight branches that you create locally and that have a name that is meaningful for you. They are where you might do work for a bug fix or feature,
(They're also called feature branches) that is expected to take some time to complete.

Another type of branch is the "remote branch" or "remote-tracking branch". This type of branch follows the development of somebody else's work and is stored in your own repository. 
You periodically update this branch (using git fetch) to track what is happening elsewhere. When you are ready to catch up with everybody else's changes, you would use git pull to both fetch and merge.


Please try these steps and let me know if you have any questions or concerns. Thank you so much for using GitHub. I hope to see you at our 5th birthday party!




### Ticket #2: Syncing internal server and GitHub?

>Hi GitHub! My company has an internal Git server used for deployments. We have an internal Git server and use GitHub. For workflow purposes, how do I sync my repository to GitHub and and the internal Git server?
>
>Thanks,
>vmg

Hint: One common option is Git remotes. There are others!


### Ticket #2 response:

Thank you so much for reaching out to me, vmg! I am more than happy to help you with this!

You can use "git remote" or "git remote -v" command to synchronize your repository to both GitHub.com and Git server. 
Before you can sync, you need to add a remote that points to the upstream repository. 
(You may have done this when you originally forked.) The command without any arguments will simply show you the remote repository aliases that it has stored. 
By default, if you cloned the project, as opposed to creating a new one locally, Git will automatically add the URL of the repository that you cloned from under the name 'origin'. 
If you run the command with the -v option, you can see the actual URL for each alias.

Please go ahead and try this and let me know if you have any questions or concerns. Thank you so much for using GitHub and have a wonderful day!



### Ticket #3:  API

>Hi GitHub!
>
>Can you show me how to make an authenticated API request?
>
>Thanks!
>newerthanyou

#### Notes:
Demonstrate a simple request to https://api.github.com/user  
https://developer.github.com/v3/users/#get-the-authenticated-user  
https://developer.github.com/v3/ (Notes on Authentication)


### Ticket #3 response:

Hello newerthanyou,

How are you doing today? I would be happy to show you how to make an authenticated API request.

The easiest way to authenticate with the GitHub API is by simply using your GitHub username and password via Basic Authentication.

		$ curl -i -u <your_username> https://api.github.com/users/user

		Enter host password for user '<your_username>':
		
Here is a source for you with more information that you will find helpful: 

https://developer.github.com/guides/getting-started/

Let me know if you have anymore questions or concerns with this.

Thank you so much for using GitHub, and have a wonderful day!
				



### Ticket #4: Unhappy about forking

>JamesTK here, I have another question.

>One of my dev collaborator forked my private repo without explicit permission to do so... is that typical? I am surprised that the system did not notify me if it was okay to grant the 
fork permission. 
Is there a way to setup permissions of this sort? Also, other than asking the collaborator to delete the forked repo, can I actually delete it?

>Thanks, jamestk

#### Notes:
You've checked the account in our admin view, he only has one personal repository (jamestk/tribbles), which has one collaborator. Any documentation you may need is available on 
[help.github.com](https://help.github.com).

### Ticket #4 response: 

Hello jamestk!

I'd be happy to help you with this.

I see that you have one personal repository, which has one collaborator.

While you can't delete a private fork of a private repository in a user account, you can do one of these things:

    Let me know if you want to request to have the fork deleted. Note that public forks of a repository that was public when it was forked cannot be deleted, even if the 
    repository is now private.
    or you can: Delete the private repository, which deletes all forks.

You can remove the collaborator by following these instructions: https://help.github.com/articles/removing-a-collaborator-from-a-personal-repository/

Thank you so much for using GitHub and please let me know if you have any additional questions or concerns.



### Ticket #5 Need to get my account back

> Hi, my name is Jorge,  
>  
> I'm the CTO of JorgeLLC. Last year, an now ex colleague, Fabian Freebird registered a github organization in name of our company. Mr Freebird has left the company in 
December 2012 and disappeared. The github organization is still registered on his account. So i would like to ask if you could transfer the organization to my account jorge2010.
>
>With kind regards,  
>Jorge

#### Notes:

* Looking at our admin view, JorgeLLC is an organization account with one owner -- freebird72
* Looking at the security history of the organization, the user jorge2010 was never a member
* Furthermore, the organization has never had another owner

GitHub does not change ownership of an account (nor will we transfer code) without a court order. This is for security reasons, to protect a legitimate owner from someone 
scamming their way into becoming the account owner. Also, it protects us from getting in the middle of a fight that we can't settle. 
We generally suggest two parties work it out themselves, since this results in faster resolution than going to court.

### Ticket #5 response:



Hello Jorge... I'm so sorry to hear that you're having this problem. 

For security reasons we are unable to to change the ownership of an account or transfer code without a court order. 
Your best bet at this point would be to work it out with your ex colleague yourself, since this results in faster resolution than going to court. 

I hope this works out well for you! Please let me know if I can be of any assistance once you get this resolved.


* Name? 

		Catharine Britt

* Location? 

		Newport, New Hampshire USA

* What's an impressionable experience you've had with customer service/support, and why?

		I would say that one of the most impressionable customer service experiences that I have had, in which I was on the receiving end, was recently I changed my cable service and I had to get a 
		new box from the cable company. I then had to call the cable co. to have them activate the box once it was plugged in. I spoke with a rep who seemed nice, and she went ahead and 
		proceeded to activate the box for me. 
		
		Now having worked in tech support for many years, I was uncomfortable with the "dead air" as she said nothing at all while we were waiting... So, I just started chatting and she ended 
		up telling me about how she lives in Boston, but would like to move, maybe to New Hampshire where I live. So I told her the best towns to look at, where she should avoid going and so on.
		We ended up having a great conversation!
		
		Basically, I felt great about that experience because I showed the lady that she doesn't have to sit there in silence, while waiting for an activation. 
		I can only hope that she applied that to calls that she received after me.


* Tell us about a time where you helped someone.

		A customer once told me that I made her "like computers again"... She went on to say that she had been having so much trouble and that other support techs
		intimidated her and made her feel stupid. She said that she liked the way I clearly explained things and that she felt comfortable working with me.
		
		I have had many other comments like this, but this particular customer had so many issues and little knowledge of computers. I found it very gratifying to help her and
		 to turn calling tech support into a positive experience for her. 


* What appeals to you about GitHub, as a company you'd potentially be working for?

		I see GitHub as a very hip company, on the cutting edge of technology, with a lot of smart, techie people. I think that there's a lot going on there and I'd love to be a part of that!
		
		
* How would you describe what GitHub does to a non-technical person?

		GitHub is an online tool for developers to store and collborate on software projects.


* What motivates you to work in support?

		I enjoy helping people and sharing my technical knowledge with them. I find it very gratifying when a tech support issue is solved, especially the challenging ones. 
		I also love showing the customers things that they may not know, to help themselves. It's also a great feeling to turn an upset customer into a happy one! 
		I've devoted my career to providing stellar tech support.


...







