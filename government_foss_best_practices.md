Government Agenicies face unique pressures in 
assessing different open source solutions;
the most important thing when selecting a FOSS project is picking one that aligns with your business goals. This is the number one requirement. You do not want to pick a project and then realize you now need to invest in a lot of effort into modifications to meet your needs. In that respect it is very similar to acquiring proprietary software.
you always want to ensure that it is actually a free and open source project and that all of the features you want to use are also free and open source. This is important because especially in niche markets there are a lot of software development companies that will either provide what is know as "open core" where the base features are FOSS, but the valuable stuff that sets them apart in the market is proprietary; or worse the project is not FOSS at all and they simply mean that you can view the source code. 
I can give you two examples that illustrate this. First it is very common for companies in competitive spaces like help desk software or document management software to release their product as FOSS. But it is also very common for them to hold back "plugins" or features that make it suitable for a a enterprise environment. For instance any time I implement a user facing application (and often even on backend products) I focused on bring in applications that integrated with my agencies single sign on system (SSO). There were lots of ways to integrate with the SSO, the most common was to use LDAP. It is very common for companies to produce open core FOSS products where you need to pay a licensing fee based on the number of uses to use their LDAP authentication plugin. 
You also need to be aware of if the license is actually a FOSS license approved by the Open Source Initiative (OSI) or the Free Software Foundation (FSF). For a long time I was considering using a "open source" compliance project to track my compliance requirements and managed my risk registry. (I had a big portfolio so InfoSec and Compliance was under me as well). The problem with this particular app was that it didn't really do much for the risk registry side and I wanted them integrated so it was easier to incorporate into my operations staff's work flow so we could operationalize compliance and move it past being a paperwork exercise. The problem with this "open source" application was that it did give me a license to see the source code, and it even gave me a license to modify it in some limited ways, but that is not FOSS. The license did not let me distribute my modifications to others, not even to other agencies groups within the government. And the kinds of modifications I could make were limited. i could have invested the time into making the modifications and upstreaming them to the company, but if they couse to incorporate them (which they didn't have to) they would also have had the right to turn around and sell my modifications back to me and other agencies in my state. Ultimately I ended up designing an implementation that used a true open source project. The modifications were a little bit more work but I had a larger to community to draw on and I knew my agency could use my work without being charged a fee.
…
integrating open source with existing government systems, cultures and compliance requirements; 
The single most common tasks I dealt with as a systems architect was working with my project managers and systems administrators to build systems integrations. Every time we acquired a new system I pushed hard to ensure that there was no data entry jobs that involved manually moving data from one agency system to another. Almost all all of my integration even between proprietary systems was done using open source tools to do the data transformations and transfers and loading. But the task was always a lot eaiser when you were working with a FOSS solution on at least one side of the integration. For that reason we choose to make complicated systems like our Identity management system keyed off of open source tools so we could guarantee that in every integrations at least once side was FOSS. Having FOSS in place gave us maximum flexibility in our integration strategy by being able to adopt one side to work around the kinks or limitations of the other side. Sure need folks to be able to log in to a Windows domain from thier desktop or to Office 365, but we feed the password changes through a FOSS OpenLDAP system to ensure that we could push password changes to all of our systems. The goal was to enable people to login into Peoplesoft (yes, that peoplesoft), their Window's Desktop, and Office 365 & Google Apps. We achieve that and more by putting FOSS at the center. 
First question is what do you mean by compliance. I used FOSS to track my compliance requirements and I used FOSS products to implement systems that were compliant with a variety of regulations (HIPAA, FERPA, PCI, various state privacy and health care requirements, NIST-800) Compliance is no harder with FOSS then it is with Propriety. If an application doesn't meet the requirements out of the box then you need to get the product configured or changed. I spent a lot of money ordering modifications to proprietary requirements to get custom modifications made to meet compliance requirements. I also spent money to get custom modifications to FOSS products by the FOSS maintainers. I would not say ordering a modification for FOSS software is any cheaper then for proprietary systems. I will say this though I was always willing to pay a premium to have the modification integrated into the mainline of the product. I typically argued for that as a contractual requirement. One reason was so I could avoid paying maintenance fees for customizations on proprietary products on an annual basis. The real reason was because customizations that aren't mainstreamed cause instability everytime you do a upgrade because it was to be reintegrated into the latest release, a task by definition never done before.The result was we would upgrade that product less often. That sucked, my customers deserved better. Any time I every paid for a modifications to FOSS software the modification was either mainstream into the core product or was released as an official plugin that got supported along with new versions of the product. Sure you might need to sponsor the upgrade of the plugin, but that is typically cheaper than the total cost of the never ending annual maintenance fees for propriety products.
I will also say it was pretty common for my team to also just use FOSS to wrap proprietary projects to bring them into compliance, or for us to make a change in-house to a FOSS project to bring it into compliance. So in that way FOSS was the way I avoided paying for custom modifications as well. Sure I had to maintain those modifications with my own staff, but I promise you the best IT staff you have has written duct tape scripts or programs to make their jobs easier and your systems more reliable or not. You are already paying that cost, because that is the right way to do IT (See e.g., DevOps and Google's SRE book). The most common modifications that we ever made was sticking applications behind a open source reverse web proxy so we could use our SSO system. (Inadequate auditing and password requirements was the most common compliance issue I dealt with). That required some modification to a lot of apps to get them to recognize the integration but often it took less then a day for one of my junior sysadmins to do, but it was always free. And because we used the same design pattern over and over again, it was very inexpensive to maintain. 
…
maintaining and securing a project built with rapidly evolving open source components; 
No harder than Proprietary systems. We found the number one key was to use FOSS libraries as much as possible that were being packed with your OS distribution so the libraries would be patched by your OS distributor and would be automatically integrated into your existing path cycles. Every propriety project requires its own patch cycle right down to figuring out how to get notifications, which I would say is the biggest hurdle that teams have to patching proprietary systems (realizing that a patch is available from that company). For inhouse projects that we could nto integrate in with our OS patching cycle because of the libraries we need to use, we built automated build systems that would pull in the latest libraries from our internal package cache. We had tools to tell use when we need to update the package cache as well, so we could control what version of the library was going into each release of our internal code. That is really cutting edge and people interest in that should look into Continuous Integration, Continuous Deployment, and DevOps to see how that happens. If your software development team is not doing those things, don't worry it is still being implemented at most companies so you have time. On the other hand if you team is not using revision control and unit tests, you are seriously behind the curve and should look at what is holding your organization back. This goes for both companies doing both internal or external development (FOSS and proprietary) using both FOSS and proprietary tools.
…
getting actively involved in an open source community; 
Just do it! I have worked at organizations that were scared to do it. Mostly because the lawyers didn't understand the risks so said "no, until we can figure it out." Or because a nontechnical person wanted to figure out how to monetize the giving away code. If you are a government agency you don't want to monetize your code, it is not worth it. You aren't a business you don't want to be. But it is worth pooling your custom code with other agencies and individuals. At the very least you get to pool the maintenance cost. But you also get happier IT staff (i.e. better retention) and you get a better reputation. And even government agencies care about their reputation. 
Simplest way is to high contractors to make modifications to the FOSS software you are using (and even if you don't know it, trust me you are) and require by contract that they publish the changes as FOSS and try to get it upstreamed. That will help you avoid lock in and you get a free third party assessment of the work quality. If your contractor gets the changes upstream then you know at least one expert liked what they did. And when you go to rebid the competitor can see exactly what they are bidding on so they can make themselves competitive by reusing what you already paid for.
Allow your staff to upstream changes and publish patches to your most important FOSS projects that they are already customizing anyways. Ask your IT folks what the product with the biggest internal changes are and work with Legal to figure out how to publish those changes. There are Licensing consultants and lawyers who specialize in this area that can help your legal team and technical team talk to and have productive conversations. 
…
finding the right contractors to work with open source; and 
Look for contractors who employee a core contributor or have multiple team members that contribute back to the project. Also look for vendors whose default is to mainstream the customizations in plugins, the main project, or a FOSS fork. They are going to be focused on selling you the new code they have to write to meet your specific needs and not trying to profit off of selling code they already wrote. That is not always possible and sometimes you really are going to ask for changes that don't make much sense to share and it would just cost to much to package up and deliver. Even then ask them to make the code repository publically available under a compatible FOSS license, so you can at least have competitive bids form other contractors in the future. If a contractor doesn't want to do this, then understand you are not buying software development services, you are buying software. The biggest advantage of FOSS is that you shouldn't have to buy software anymore. It is a zero margin good, we need to move towards paying money to make technology better, not paying money to just get to what some else already paid to be created.
…
contributing government code back into the public domain. 
Contributing back depends on what kind of government agencies you are. If you are federal agency you probably dont have copyright so you can look at code.gov. But see some of the recent work being done at code.mil, Most agencies have opt for using the Creative Commons Public Domain dedication/license (CC0). But also check out how the DoD is positing itself to use copyleft licenses for its projects to protect its invests from becoming closed source.
If you are a state agency you need to find out what your state's law on copyright ownership is. Most states retain the copyright in works they produce, but often have some exceptions. For instance the state of connect lets employees at one of its universities retain the copyright, but not at most of the other ones. But in this respect States are not any different then a nonprofit or a for profit company. I think both federal and state agencies need to recognize that if Google and Oracle and Redhat and Microsoft can release and some cases sell FOSS software that is okay for them to do it. Oracle is a very conservative company but is uses these licenses. It is not that risky if the folks are doing it. And more importantly they figured out how to do it, so government agencies shouldn't think they need to reinvent the wheel. There is a solid roadmap for how to do it. 