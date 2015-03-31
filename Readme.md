# Dokku Make Hook

Hook into dokku plugins from your Makefile. Supported on dokku `0.3.15`.

## Installation

Log into your server and run:

    git clone https://github.com/matthewmueller/dokku-make-hook /var/lib/dokku/plugins/make-hook

## Example Makefile

```make
production:
  NODE_ENV=production node app.js

dokku.post-build-buildstep:
  duo-bundle app.{js,css}

dokku.post-deploy:
  slack "deploying!"
```

## Event list

You can find what each of the events do here: http://progrium.viewdocs.io/dokku/development/pluginhooks

    - post-build-buildstep
    - post-build-dockerfile
    - post-deploy
    - pre-deploy
    - pre-delete
    - pre-release-buildstep
    - pre-release-dockerfile

> Accepint PRs for the other events. From my testing, it seemed that
the other ones modified state, which would break the process in
unexpected ways
