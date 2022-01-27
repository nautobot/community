# Nautobot Community Meeting - 2022-01-27 

Agenda: https://github.com/nautobot/community/issues/20

## Announcements & Reminders!

`jathanism`: We wanted to say thank you to the community contributions for the following features:

- [Introduction of Provider Networks · #1144](https://github.com/nautobot/nautobot/pull/1144) by @johannwagner

- [Add support for Python 3.10 · #1255](https://github.com/nautobot/nautobot/pull/1255) by @alextremblay

`jathanism`: Reminder: We want your contributions. Your code is good enough and we will be gentle (yet firm).

## Stale Pull Requests Review

### Change cache health_check nautobot ([#811](https://github.com/nautobot/nautobot/pull/811))

`jathanism`: There's still lingering PR review comments and some merge conflicts. This one was brought up in November, and we would still like to see it finished!

## Q&A about Upcoming Features

### Add Support for Dynamic / Arbitrary Groups of Objects ([#896](https://github.com/nautobot/nautobot/issues/896))

`jathanism`: Dynamic Groups. This is a complex feature and we have a prototype in the works for it. We would love your eyes and ears on this one.

> `jathanism`: Protoype PR here: https://github.com/nautobot/nautobot/pull/1047

### Docker images now default to Python 3.7 ([#1252](https://github.com/nautobot/nautobot/pull/1252))

> `jvanderaa`: For Docker, would it make sense to move forward to 3.9 and the reported performance increases?
>
> `jvanderaa`: Or is there a tie in from a development perspective to these containers that then need to remain at the lowest base level?
>
> `glennmatthews`: We ship containers for 3.6-3.9 at present and will be adding 3.10 soon. So this is really just about what we consider to be the “default” image. I certainly wouldn’t be opposed to re-evaluating which version we want to consider as default, especially if it does bring in other improvements. (3 :+1:)

### Provider Network Model ([#724](https://github.com/nautobot/nautobot/issues/724))

### Add JSON type for custom fields ([#897](https://github.com/nautobot/nautobot/issues/897))

### Explore adding a concrete Job model ([#1001](https://github.com/nautobot/nautobot/issues/1001))

`jathanism`: We will be prototyping this soon.

## New Ideas/Proposals that need traction/attention

### Drop Support for Python 3.6, Add Support for Python 3.10 ([#1268](https://github.com/nautobot/nautobot/issues/1268))

`jathanism`: This one is somewhat contentious but we are pretty sure we will be going forward with it, predominantly for security reasons.

> `ggiesen`:  I think this is a bit of a mistake. 3.6 is still the default Python on RHEL 8/AlmaLinux 8/Rocky Linux 8/insert flavour here. Security fixes will be backported to these platforms for some time to come. I was under the impression that part of the reason for the creation of Nautobot was avoid the treadmill of upgrades and create some long term support. This would seem to go against that
> 
> `jathanism`:  The problem we are facing are high severity security fixes in dependent libraries that themselves are dropping support for Python 3.6 This puts us into a challenging situation to fork and backport dependencies on our own, or dropping support for Python 3.6 entirely.
> 
> `jathanism`:  Python 3.6 is EOL as of 2021-12-31 and will no longer receive security or bug fixes.
> 
> `ggiesen`:  yes I realize the Python project has deprecated support for it
> 
> `ggiesen`:  But the distribution vendors have not
> 
> `jathanism`:  So just to be clear, your concerns are valid. We definitely want to come up with a path forward that tries to take these into account.
> 
> `jathanism`:  `ggiesen` What is the take on your environment for having applications in with unpatched CVEs? (e.g. Nautobot v1.2.4 using Python 3.6 would have two unpatched high severity CVEs because of dependencies. Celery and Pillow in this case.) (edited) 
> 
> `ggiesen`:  I'm not sure what the right answer is. I know distributions are committed to backporting fixes to 3.6, but that doesn't help you with dependencies. I also know there are AppStreams for later python versions, but not sure how well that plays if you have multiple python versions on the same box (edited) 
> 
> `jathanism`:  Right yeah it's difficult because obviously we also don't have the vast resources that a company like Red Hat has to consistently maintain backporting security fixes into applications we don't own or maintain ourselves.
> 
> `jathanism`:  `ggiesen` Thank you for input. We don't take it lightly!
> 
> `bryanculver`:  `ggiesen` I hope I captured your concern well in the GitHub issue linked above. If there is any other information or thoughts you would like to share, feel free to add them here or the issue itself.
> And thank you for bringing this to our attention.
> 
> `Tyler Bigler`:  I think it’s plenty reasonable to end support once the ‘primary’ maintainers have stopped supporting it. Python 3.6 is over 6 years old (woah) now. RHEL8 has does have “official” ways of getting more current versions of Python as you said
> 
> `Tyler Bigler`:  I’m amazed that RHEL8's shipped default is 3.6
> 
> `Tyler Bigler`:  It doesn’t invalidate your concern of course - but it becomes a mountain to balance the longer you hold on to supporting really old stuff.
> 
> `jathanism`:  I’m amazed that RHEL8's shipped default is 3.6
> Same. Python 3.6 was already old when RHEL 8 shipped in 2019!
> 
> `Tyler Bigler`:  3.7 was about a year old by then too
> 
> `Tyler Bigler`:  Just crazy
> 
> `jvanderaa2`:  I agree that it is crazy that it came as default on the timeline. I also know that Ansible is now requiring minimum Python of 3.8. With Ansible being owned by RedHat, it is an interesting library to compare to

### Long Term Support (LTS) Releases ([#1291](https://github.com/nautobot/nautobot/issues/1291))

`jathanism`: As we move closer to our v2 horizon, we need to think about LTS for v1.x users.

### Project housekeeping improvements ([#1276](https://github.com/nautobot/nautobot/discussions/1276))

`jathanism`: We are considering automated dependency upgrades using Renovate, and possibly moving the base Docker image to something like Google Distroless? Possible other automated housekeeping solutions?

(1 :+1:)

> `bryanculver`: The topic of changing our base image to something even leaner/“slim”-er than we are already have was started to address CVEs inside the base image `python-slim` is based off of that are still unfixed. This has been presenting itself as challenges with deploying in some environments that have a scan enforcements. Link to that discussion here: https://github.com/nautobot/nautobot/issues/1111 (1 :closed_lock_and_key:)

## Q&A and FYI about Developer Experience

`jathanism`: We don't have anything completed right now as we are just entering the v1.3.0 development cycle. Here is some work in flight.

### Reorganize the Contributor Workflow documentation ([#1293](https://github.com/nautobot/nautobot/pull/1293))

### Spike: Explore and test GraphQL subscription support ([#586](https://github.com/nautobot/nautobot/issues/586))

(1 :+1:)

### Implement user guide for working with custom fields ([#270](https://github.com/nautobot/nautobot/issues/270))

### Explore Plugin registration and deregistration ([#16](https://github.com/nautobot/nautobot/issues/16))

### Consolidate the two development environments to a hybrid (virtualenv + Docker) approach ([#507](https://github.com/nautobot/nautobot/issues/507))

## Open Discussion & Forum

`jathanism`: We'll leave this open for a bit in case you have any direct questions we haven't covered that you want answered by the core team. Give us your worst!

## Post-Meeting Feedback

`ggiesen`: I think this might work better as a Zoom call with an agenda to go through these item by item. I know it's not as accessible, but may drive more engagement (2 :point_up:)