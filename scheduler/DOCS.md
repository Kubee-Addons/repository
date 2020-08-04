# Kubee Scheduler

Scheduler Addon ...

This addon give us the possibility to handle a simple week configuration of automation, light, binary_sensor, climate, cover, switch and script.

![main](https://raw.githubusercontent.com/kubee-addons/addon-schedulerler/master/main.png)

Entity setting section:

We can made a group and set on or off action every day with follow format:

- No Fill -- ( No action on this day)
- HH:MM:SS - ( Time format )
- sunrise/sunset - ( Action at sunrise/ sunset - sunrise/sunset )
- sunrise+30M   (M = Minutes, S = Second) - ( Offset + or - at sunrise or sunset )  
- :T27 - (:T + temperature to set) BETA

![edit](https://raw.githubusercontent.com/kubee-addons/addon-schedulerler/master/edit.png)

## Installation

Copy the url of this addon into "Supervisor" -> "Addon Store" -> "Add New repository URL" after install it.

## Configuration

log_level: Level of logging messages default info
max_retries: Number of retrying action default 2
max_retry_interval: How many seconds to wait before retrying. default 5
bk_color: The background color default vaule #f8f9fa (white)

## Kubee service

There is the possibility to enable or disable an entity by call these service on you automation/script:

```yaml
service: hassio.addon_stdin
data:
  addon: 998c1fd8_homeassistantscheduler
  input: light_group:enable_on
```

addon = name of addon
input = group name:action (enable_on or enable_off)

## Scheduler

Portainer is an open-source lightweight management UI which allows you to
easily manage a Docker host(s) or Docker swarm clusters.

It has never been so easy to manage Docker. Portainer provides a detailed
overview of Docker and allows you to manage containers, images, networks and
volumes.

## WARNING

The Portainer add-on is really powerful and gives you access to virtually
your whole system. While this add-on is created and maintained with care and
with security in mind, in the wrong or inexperienced hands,
it could damage your system.

## Scheduler Installation

The installation of this add-on is pretty straightforward and no different
compared to installing any other Home Assistant add-on.

To be able to use this add-on, you'll need to disable protection mode on this
add-on. Without it, the add-on is unable to access Docker.

1. Search for the "Portainer" add-on in the Supervisor add-on store and
   install it.
1. Set the "Protection mode" switch to off.
1. Start the "Portainer" add-on.
1. Check the logs of the "Portainer" add-on to see if everything went well.

## Scheduler Configuration

**Note**: _Remember to restart the add-on when the configuration is changed._

Example add-on configuration:

```yaml
log_level: info
agent_secret: password
```

**Note**: _This is just an example, don't copy and paste it! Create your own!_

### Option: `log_level`

The `log_level` option controls the level of log output by the addon and can
be changed to be more or less verbose, which might be useful when you are
dealing with an unknown issue. Possible values are:

- `trace`: Show every detail, like all called internal functions.
- `debug`: Shows detailed debug information.
- `info`: Normal (usually) interesting events.
- `warning`: Exceptional occurrences that are not errors.
- `error`:  Runtime errors that do not require immediate action.
- `fatal`: Something went terribly wrong. Add-on becomes unusable.

Please note that each level automatically includes log messages from a
more severe level, e.g., `debug` also shows `info` messages. By default,
the `log_level` is set to `info`, which is the recommended setting unless
you are troubleshooting.

### Option: `agent_secret`

An option to set a shared agent secret. Must also be set in the remote agent
as an Environment variable.

## Known issues and limitations

By default all Home Assistant managed containers are hidden from Portainer.
This is recommended since fooling around with Home Assistant managed containers
can easily lead to a broken system.

Access to these containers can be gained by going into Portainer ->
Settings -> Hidden containers. Then delete the listed hidden labels
(io.hass.type labels). **Only do this if you know what you're doing!**

## Changelog & Releases

This repository keeps a change log using [GitHub's releases][releases]
functionality. The format of the log is based on
[Keep a Changelog][keepchangelog].

Releases are based on [Semantic Versioning][semver], and use the format
of ``MAJOR.MINOR.PATCH``. In a nutshell, the version will be incremented
based on the following:

- ``MAJOR``: Incompatible or major changes.
- ``MINOR``: Backwards-compatible new features and enhancements.
- ``PATCH``: Backwards-compatible bugfixes and package updates.

## Support

Got questions?

You have several options to get them answered:

- The [Home Assistant Community Add-ons Discord chat server][discord] for add-on
  support and feature requests.
- The [Home Assistant Discord chat server][discord-ha] for general Home
  Assistant discussions and questions.
- The Home Assistant [Community Forum][forum].
- Join the [Reddit subreddit][reddit] in [/r/homeassistant][reddit]

You could also [open an issue here][issue] GitHub.

## Authors & contributors

The original setup of this repository is by [Romeo Covaci][Romeo].

For a full list of all authors and contributors,
check [the contributor's page][contributors].

## License

MIT License

Copyright (c) 2018-2020 Romeo Covaci

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[contributors]: https://github.com/kubee-addons/addon-portainer/graphs/contributors
[discord-ha]: https://discord.gg/c5DvZ4e
[discord]: https://discord.me/hassioaddons
[forum]: https://kubee.ga/68836?u=Romeo
[romeo]: https://github.com/romeocovaci
[issue]: https://github.com/kubee-addons/addon-portainer/issues
[keepchangelog]: http://keepachangelog.com/en/1.0.0/
[reddit]: https://reddit.com/r/kubeeapps
[releases]: https://github.com/kubee-addons/addon-portainer/releases
[semver]: http://semver.org/spec/v2.0.0.htm
