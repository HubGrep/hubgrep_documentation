
## Development Setup

Create a config by copying `.env.dist` to `.env`, and add the missing values.

Then start the service and database

    docker-compose up

Run the initial migration in the container:

    docker-compose run --rm hubgrep_indexer /bin/bash
    flask db upgrade

### Add a Hosting Service

To actually do something, you need to add a Hoster as well.
This could be done via cli. Right now there is only 

    flask cli import-hosters <path/to/hosters.json>

Where the `hosters.json` should have a list of Hosters, looking like this:

```
[
  {
    "type": "gitlab",
    "landingpage_url": "https://gitlab.freedesktop.org/",
    "api_url": "https://gitlab.freedesktop.org/",
    "hoster_name": "gitlab.freedesktop.org",
    "api_key": ""
  },
  {
    "type": "gitlab",
    "landingpage_url": "https://gitlab.com/",
    "api_url": "https://gitlab.com/",
    "hoster_name": "gitlab.com",
    "api_key": ""
  },
  {
    "type": "gitea",
    "landingpage_url": "https://codeberg.org/",
    "api_url": "https://codeberg.org/",
    "hoster_name": "codeberg.org",
    "api_key": ""
  },
  {
    "type": "gitea",
    "landingpage_url": "https://gitea.com/",
    "api_url": "https://gitea.com/",
    "hoster_name": "gitea.com",
    "api_key": ""
  },
```

(Github is the only hoster that actually needs an api key - for all others, just leave it empty)

Afterwards you should  be ready to set up and start a crawler!


