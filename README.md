This document contains Frequently Asked Questions regarding the technical stack behind WECHANGE.

If you can't find an answer to your question you can:
* Join our Discord chat at https://discord.gg/pX2TJMM
* Join our weekly meeting on Wed 2-3pm CEST at https://meet.jit.si/wechange
* Create an issue within this repo
* Create a pull request for your question/answer within this repo

Greetings from Berlin and Munich,
Michael (CEO), Sascha and Simon (Technology)

# Table of contents

* General / Onboarding
  * [Who develops WECHANGE/cosinnus?](#developers)
  * [What is the current development model of the software?](#development-model)
  * [On Github there are only few people and little activity. Many points of further development could be developed openly together. Why doesn't that happen much yet?](#community)
  * [WECHANGE seems to be a company, do I have to contact if I want to use the software?](#get-in-contact)
  * [Are you really open source? A lot of documentation and manuals seem to be missing.](#open-source)
  * [Where can I find more documentation?](#documentation)
  * [How can I get involved?](#get-involved)
* Onboarding
* Open Source Policy / License
* Data protection / Privacy
* Security

# General / Onboarding
<a id="developers"></a>
## Who develops WECHANGE/cosinnus?
In addition to 2 concepters, WECHANGE currently employs 2 developers who fix upcoming bugs and develop features in this framework. Currently, the project is being developed in the context of customer inquiries, funding projects (mainly from the Foreign Office), feature requests and white label portals. Using open source code and modules complies with our claim to transparency and disclosure. Our mission is to create maximum synergy, visibility, connectivity and collaboration. 

Therefore, it has not been useful and necessary to develop and set up closed systems. Against the background of this networking idea, but also for security and stability reasons, we will develop a public (preferably federated) interface for the exchange of data between WECHANGE platforms and other platforms from the change spectrum with which we already cooperate (such as eg www.kartevonmorgen.org). The Github project was just the first step in building an open source developer community. We look forward to taking further steps with you or other interested developers, should that be in your interest.

<a id="development-model"></a>
## What is the current development model of the software?
The software behind the platform "wechange.de" is "cosinnus". There are currently 8 Platforms that use and develop this software (license is AGPL). The main platform wechange.de still cannot finance the further development by revenues generated groups and portals. Therefore the development is strongly geared to available finances and financing partners, currently especially our portal customers, who finance the further development.

<a id="community"></a>
## On Github there are only few people and little activity. Many points of further development could be developed openly together. Why doesn't that happen much yet?
Exactly. Even though we would like to, unfortunately there is no open source community yet. So far, there has been only temporary support from other developers in hackathons. You're invited to change this by contributing.

<a id="get-in-contact"></a>
## WECHANGE seems to be a company, do I have to contact if I want to use the software?
Of course you do not have to contact us for any project. This is an offer that can be performed on request. We assume that most people are grateful to receive a portal that we manage reliably. At the same time, this service is an important building block for the economic operation of our cooperative. We are happy to go new or different ways with you (currently, for example, tailwind from the GLS Bank indicates) and look forward to working together.

<a id="open-source"></a>
## Are you really open source? A lot of documentation and manuals seem to be missing.
The core initiators network n, Förderverein Wachstumwende and Transition Town had at that time not the claim of a complete open source solution, but wanted to use the resources available to know the maximum feature set funded. As part of the Cooperative Statute, we then determined that each user must use all existing features and co-finance roll-out on all platforms.

As a cooperative, we have been striving to further develop and, among other things, build the project for a true open source project, but are currently still focusing on stabilizing our business model. Advertising measures, especially by third parties, are not part of our business model and are not planned for the future.

<a id="documentation"></a>
## Where can I find more documentation?
We are currently only 1.5 developers and would like to have a more detailed documentation of the individual steps. Unfortunately, we simply did not have enough resources for that. As a result, we have provisionally offered our personal support by e-mail or discord channel. Among other things, in August 2019 we will be holding a hackathon with the Belarusian NGO "Falanster" on the subject of maps, interfaces and documentation, funded by the Federal Foreign Office as part of a project to expand the cooperation of civil society actors from Russia, Germany and countries of the Eastern Partnership. For this you are cordially invited. https://www.auswaertiges-amt.de/de/aussenpolitik/europa/erweiterung-nachbarschaft/nachbarschaftspolitik/zivilgesellschaft-projekte-oestliche-partnerschaft/301008

<a id="get-involved"></a>
## How can I get involved?
We're still working on our onboarding process. For now please:

* Join our Discord chat at https://discord.gg/pX2TJMM
* Join our weekly meeting on Wed 2-3pm CEST at https://meet.jit.si/wechange

# Setup
## Can I setup WECHANGE locally (for development) or on my own server?
The project is completely downloadable and executable. There are two options for this, which are also documented at https://github.com/wechange-eg/cosinnus-devops in the form of commands:

* Using docker: The Docker setup was created during a hackathon in 2017 (it was working) and is currently not used by us for development, it definitely requires care. If you prefer to use that, we'll be happy to help you update and complete the setup. For the start, the manual setup is better.
* Manually: As usual for Python projects, git clone / virtualenv / pip is used. The setup is unfortunately not quite trivial because of the dependencies to other open source projects - we are happy to bring the Docker image up to date together. In the last hackathon, the participants were able to set up the project locally with the help of the instructions. However, instructions are still missing for setting up the dependencies Etherpad, Ethercalc and (not required) ElasticSearch. We will supplement this with references to the installation instructions for these projects.

## Where do I find documentation about the production setup?
The most important difference is the DEBUG setting (in production "False"), which is also the basis for other settings. If you have any questions about the infrastructure required, please refer to COMMUNITY.

# Data Protection / Privacy
## Why do you use web statistics?
[9] Despite being Open Source unfortunately we still cannot dispense with tracking web statistics. We use them to evaluate the success of funded projects, which still make part of our financial basis. However we use the Open Source Web Analytics Platform Matomo (Piwik) and we've taken all known measures within Matomo to protect privacy. For example, we mask the IP address (2 bytes, also used to prepare the visits), use the Do-Not-Track support and let users opt out of tracking. That's why e. g. for analysis of attacks (eg DDOS) the web statistics are not really helpful. Of course, the settings are site specific, i. you could change settings for your own portal or remove the tracking code completely.

## When do you delete the tracking data collected?
The data is being deleted automatically by Matomo after 30 days.

## When combining thw two session cookies used (WECHANGE and Matomo), the data can still be assigned to people even after anonymisation.
Good hint. Theoretically, the session ID of WECHANGE can be matched with the session ID of Matomo. Since the session ID in Piwik can not be read out so easily, we consider this as secondary. We are happy to work together to come up with a better solution and implement it.

## When a user is being deleted, the contributions don't get erased but only anonymized. This is not enough, since according to GDPR there's a right for complete cancellation. The user name could also appear within contributions (e.g. posts). 
Cancellation (german: „Löschen“) does not mean destroying (german: „Vernichten“). To our knowledge anonymizing is considered as cancellation within the meaning of the GDPR. If that is not enough, we can also build another solution together.

## For contact form and email communication you save message and complete sender data. Any information added by an e-mail program need not and should not be saved. This is information that you do not need for further processing of an e-mail.
This is common practice and from our point of view, no further concern. If you have a good alternative solution, we are open to it.

## Why do you use Mailjet for sending emails?
We recently switched  to Mailjet, a specialized provider that works with EU-compliant privacy policies. We work with this provider to ensure the successful delivery of over 100,000 emails per month, which would not be possible at Hetzner. Please let us know, if you know about a more suitable provider.

## Do you still use SSL somewhere?
We are aware that SSL is no longer considered secure. To our knowledge, we now use only TLS.

## Why do you want to leave a cookie active for 30 days?
We try to find the best balance between users concernced about privacy and users focussed on usability. There are a lot of very active users, who do not want to log in all the time.


# Security
## Why don't you use common technologies such as HSTS (or any other safety precaution)?
We're giving our best to provide maximum and data security while maintaining the current usability of the platform. Please get in contact with us directly regarding any security concerns. 

## According to the law the police can copy data from your hoster (Hetzner) without informing you (WECHANGE). Therefor WECHANGE also won't be able to inform users about potential accusasions (or worse).
Good hint, we are aware of that. Above all, we are with Hetzner for financial reasons. But we are already in negotiation with https://www.hostsharing.net/ and will raise the issue there again. Whether this can be avoided is not yet clear to us.


# Features / Integrations
## Why did you decide for Rocket.Chat, which is not considered current in the area of privacy and group chats?
The Rocket.Chat integration is being implemented by platform "platform-n.org" with the WECHANGE eG. After much consideration (most recently between Matrix and Rocket.Chat), we chose Rocket.Chat for usability and product maturity. Although we're in love with the concept behind Matrix, initial tests with users have shown that we can not yet use Riot as client. Reasons were above all design, adjustment possibilities and risk of the data loss (key management is left to the user).

E2E encryption is possible with both. Fortunately, both Matrix and Riot seem to be evolving faster and faster, and we can imagine switching back in the future or even running individual platforms with a different client. The integration currently happends via iframe and webhooks.

## Is it possible to get privacy and security concepts? The FAQ states that the pentest in 2015 has confirmed good data protection. Also the details of the security concept would be interesting. How often do you make backups? How does the platform scale?
The data protection report of the pen test by german TÜV is no longer up to date. Another pen test would be useful in the meantime, but unfortunately we didn't manage to finance it yet. We have implemented all the necessary data protection measures within the framework of the GDPR, but we have so far largely lacked such a security concept. Therefore, it is one of our declared TOP goals for 2019 to create such a security concept with experts. In the meanwhile, please get in contact with us directly if you have questions or you are an expert.
