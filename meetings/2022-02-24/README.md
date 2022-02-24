# Nautobot Community Meeting - 2022-02-24 

Agenda: https://github.com/nautobot/community/issues/22

## Announcements & Reminders!

### Dropping 3.6 Support in 1.3 ([#1268](https://github.com/nautobot/nautobot/issues/1268))

`bryanculver`: After careful review, we think it will ultimately be the better direction to drop 3.6 support in the next upcoming minor release, 1.3 (tentatively end of March).

`bryanculver`: We are aware some distros still support 3.6 by backporting fixes, but our concerns largely stem from unsupported Python packages, not necessarily the language itself.

### Patching Release Schedule

`bryanculver`: We have adopted a formal patching schedule. Every two weeks, on Mondays, starting March 7th, we will release a new patch release of all items merged into `develop`. We have more details on that in our RTD ([link here](https://nautobot.readthedocs.io/en/stable/development/#patch-releases))

### Upcoming Beta Release of 1.3

`bryanculver`: Be on the lookout in the next couple weeks as we aim to get the first beta of 1.3 out. We will be getting more frequent and earlier beta releases out so users can get their hands on them and provide feedback sooner.

## Stale Pull Requests Review

### Closing PR [#811](https://github.com/nautobot/nautobot/pull/811) (Change cache health_check nautobot)

`bryanculver`: We will be closing PR #811 by tomorrow. There hasn’t been attention to lingering feedback, and seemingly no community interest. We will gladly revisit it if someone is interested in taking up the remaining work.

## Q&A about Upcoming Features

`bryanculver`: When we drop the beta of 1.3, we will be looking for feedback on the initial implementations of two new features:

- Add Support for Dynamic / Arbitrary Groups of Objects ([#896](https://github.com/nautobot/nautobot/issues/896))

- Concrete Job Model ([#1001](https://github.com/nautobot/nautobot/issues/1001))

`bryanculver`: PRs near ready to merge for them to hit `next` soon, and we will have some corner cases we will address in followup to the beta, but core functionality should be complete by then.

`bryanculver`: Also, merged into `next` already is the Provider Network Model ([#724](https://github.com/nautobot/nautobot/issues/724)) which is a community contribution :tada: and we would love feedback on this whenever it’s available.

## New Ideas/Proposals that need traction/attention

### Adding Thycotic Secret Provider to the Nautobot Secrets Providers Plugin ([#22](https://github.com/nautobot/nautobot-plugin-secrets-providers/pull/22))

`bryanculver`: Another great community contribution. There was a question around when this could be brought in, or if it would force moving to 3.7 before 1.3, however we would like to see this available now for those already on 3.7+. Therefor since it is an optional plugin, it will just be a matter of documentation and conditional optional dependency specification. We are working on getting this over the finish line.

### Plugin Capability to Add Tabs to Core Object Detail Views ([#1000](https://github.com/nautobot/nautobot/issues/1000))

`bryanculver`: (from just before the community meeting)

> Think #1000 may be able to get looked at/considered for 1.3?

`bryanculver`: This feature is not currently in scope for 1.3.

## Q&A and FYI about Developer Experience

`bryanculver`: Some new features coming in the 1.3 beta that should :+1: developer experience:

- Per-Job Soft and Hard Time Limits ([#885](https://github.com/nautobot/nautobot/issues/885))
- Ability to Hide a Job in UI ([#863](https://github.com/nautobot/nautobot/issues/863))
- Job Meta Description Now Supports Markdown Formatting ([#916](https://github.com/nautobot/nautobot/issues/916))

## Open Discussion & Forum

### Downloading Job Output (from `Josef`)

> `Josef`: Hi, Is there an easy way to download the job output without copy paste?
> 
> `jathanism`: From the Job Results API endpoint for that job's result, you can get that value from the data field.

### Community Jobs Library (from `Josef`)

> `Josef`: Is it planned to add a community jobs library repository?
> 
> `jathanism`: Nothing currently planned but it's a great idea! We would be open to that.
> 
> `Glenn M`: This would especially tie in to some of the enhancements coming in under the Concrete Job Model feature - as an admin or power user now has the ability to selectively enable/disable individual jobs from a Git repository as being runnable or not
> 
> `Josef`: cool
> 
> `jathanism`: At this point it would probably make sense to do it for post-v1.3.0 jobs as you probably noticed we are putting a lot of emphasis on them.
> 
> `Josef`: Everything is fine. I recognized that I had data inconsistencies (rear port without front port) and having such data quality jobs in a library will save time for all

### Community Meeting Alternatives (from `Josef`)

> `Josef`: Is there a plan to switch from Slack to another tool. The searchable history is very restricted
> 
> `jathanism`: Noooooo not anytime soon. But we do want to continue to encourage using GitHub Discussions for things that require persistence or long-running conversation.