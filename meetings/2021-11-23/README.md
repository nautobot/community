# Nautobot Community Meeting - 2021-11-23

Agenda: https://github.com/nautobot/community/issues/11

## Announcements & Reminders!

`jathanism`: Nautobot 1.2.0b1 is out, feedback will be valuable!

`jathanism`: We would very much like to have 1.2.0 out the door early December, however we can't rush quality!

##  **Stale Pull Requests Review**

`jathanism`: Here are the stale pull requests we want to review:

- [Change cache health_check nautobot#811](https://github.com/nautobot/nautobot/pull/811) (changes requested on 1 October)
- [Fix graphql restart on relationship change nautobot#925](https://github.com/nautobot/nautobot/pull/925) (not an easy problem to solve; proposed solution needs to be reviewed in depth by core team)

> `kcelenza`: This one would be great to get in, is this being reviewed for 1.2?
>
> `jathanism`: We are trying. This one has turned out to be quite a challenge.
>
> `jathanism`: The core issue being that the schema object is generated in the main thread, and it becomes difficult in a multi-threaded server environment to replace it once running.
>
> `jathanism`: The current experimentation is using a cached singleton pattern where the schema is always retrieved from Redis at call time. We just have yet to button that up, assuming it's the one we stick with. (edited) 

- [Programmatic validation for table fields (WIP) nautobot#1029](https://github.com/nautobot/nautobot/pull/1029) (draft, pending review by core team)
- [Add dumpdata and loaddata description nautobot#1046](https://github.com/nautobot/nautobot/pull/1046) (updated by submitter, needs re-review by core team)
- [Doc: How to search for users in multiple LDAP groups nautobot#1080](https://github.com/nautobot/nautobot/pull/1080) (pending review by core team)

`jathanism`: Please reply to each in a thread if you have any comments. Just a general comment that we are still working on lingering bugs and PRs as we close in on the final release.

## Q&A about Upcoming Features

### GraphQL multi-level filtering ([#799](https://github.com/nautobot/nautobot/pull/799))

### Secrets, groups, and providers [#868](https://github.com/nautobot/nautobot/pull/868))

> `Eric Jacob`: Is there any documentation available explaining how to write a custom provider?
>
> `Eric Jacob`: Also, will it be possible to use the secrets with "nautobot_plugin_nornir"? It is not clear for me how this beast will work...
>
> `jathanism`: No dev docs yet
>
> `jathanism`: https://github.com/nautobot/nautobot/blob/develop/nautobot/extras/secrets/providers.py#L15-L35
>
> `jathanism`: But providers are pretty basic. You give them a name, slug, define an inner `ParametersForm` for the required inputs, and th en a `get_value_for_secret()` method that returns the secret value.
>
> `jathanism`: a `Secret` instance gets passed to that method
>
> `jathanism:` We will be publishing an open source plugin w/ providers for AWS Secrets Manager and HashiCorp Vault soon.
>
> `Eric Jacob`: As for the "nautobot-plugin-nornir", it also has a Credential Manager. Will it be possible to use the new secrets integration feature with it?
>
> `jathanism`: @kcelenza I think it's safe to say "yes eventually" here, but perhaps not immediately at 1.2 launch since it would need to be adapted? (edited) 
>
> `kcelenza`: I am trying to get it in by 1.2 release
>
> `kcelenza`: no guarantees. But will release a golden config 1.0 after nautobot 1.2

### Admin configuration ([#1079](https://github.com/nautobot/nautobot/pull/1079))

> `Eric Jacob`: Will plugins be able to use the same mechanism?
>
> `jathanism`: Great question! We have started the groundwork for plugins to be configurable form within the UI, but nothing quite ready for showtime yet. There is technically nothing stopping plugins from extending the configurable options, but we have not yet documented it.

### Job scheduling/approval (this is complicated one)

### Organizational branding ([#924](https://github.com/nautobot/nautobot/pull/924))

### Enforce number of concurrent Jobs running at the same time ([#1004](https://github.com/nautobot/nautobot/issues/1004))

## New Ideas/Proposals that need traction/attention

`jathanism`: These are specifically things on which we would like community input.

### Contact modeling ([#1071](https://github.com/nautobot/nautobot/discussions/1071))

### Multiple untagged VLANs on an interface ([#1045](https://github.com/nautobot/nautobot/discussions/1045)) 

### More generalized Reservation model ([#1033](https://github.com/nautobot/nautobot/discussions/1033))

### Segment Routing modeling ([#1014](https://github.com/nautobot/nautobot/discussions/1014))

> `Josh Dickman`: fwiw I’m working on a plugin for exactly that: https://github.com/josh9730/refactored-couscous/tree/nautobot/apps/nautobot_app_sid. Didn’t include SRGB since best practice is to use the same SRGB domain
>
> `jathanism`: Wow, @Josh Dickman! Thanks for letting us know. It would be great to have your contribution on that discussion thread!

### REST API endpoint for token management ([#471](https://github.com/nautobot/nautobot/discussions/471))

## Q&A and FYI about Developer Experience

`jathanism`: These are features coming in 1.2.0 that plugin authors should know about!

### New plugins list view and detail view, link pattern for plugin "home" and "config" views ([#935](https://github.com/nautobot/nautobot/pull/935))

### `nautobot_database_ready` signal ([#820](https://github.com/nautobot/nautobot/pull/820))

### Plugin defined banners ([#756](https://github.com/nautobot/nautobot/pull/756))

### New object detail view base template ([#737](https://github.com/nautobot/nautobot/pull/737))

### Software defined home page, extensible by plugins ([#716](https://github.com/nautobot/nautobot/pull/716))

## Open Discussion & Forum

`jathanism`: We do have one discussion topic provided by the community:

- [Centralised collection of nautobot common commands (#911)](https://github.com/nautobot/nautobot/issues/911)

> `jathanism`: My initial reaction to this suggestion is positive, however I think of the logistics for it being specific to our production Linux deployment instructions.I think in that context it seems like a good idea. I am wary of whether trying to have a one-size-fits-all approach to a command matrix would be tenable.
>
> `danielfjteycheney`: I'm not quite understanding the response here. Just so I understand, are you saying that due to there being many flavours of Linux, such a table of centralised commands wouldn't be tenable?Just to explain where I'm coming from, there are a lot commands that could be centralised to help developers diagnose their own problems before creating issues on Slack. Most of us like to solve problems ourselves if there was some central page to look/understand what commands do.
>
> `jathanism`: My apologies if I was terse. My preference would be to keep it specific to supported operating systems. Red Hat and Ubuntu are similar enough but they are not identical.I like the idea, I just want to be considerate of the various deployment methodologies we currently support: Linux manual deployment, Docker, and Kubernetes. I could see your proposal being useful if we can document and cross-reference without having to duplicate documentation!

## Closing Remarks

`jathanism`: We'll go ahead and conclude for today, seeing as it's a holiday week and we had to move it! Please feel free to reply to any of the threads from today and we'll address them. And have a great holiday week.
