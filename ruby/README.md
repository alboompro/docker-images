# Ruby images

Production mode to best performance running at kubernetes.

## Versions

- [3.1 base](3.1/stretch) - [3.1 with nodejs](3.1/stretch/nodejs) - [3.1 full](3.1/stretch/full)
- [3.0 base](3.0/stretch) - [3.0 with nodejs](3.0/stretch/nodejs) - [3.0 full](3.0/stretch/full)
- [2.7 base](2.7/stretch) - [2.7 with nodejs](2.7/stretch/nodejs) - [2.7 full](2.7/stretch/full)
- [2.6 base](2.6/stretch) - [2.6 with nodejs](2.6/stretch/nodejs) - [2.6 full](2.6/stretch/full)
- [2.5 base](2.5/stretch) - [2.5 with nodejs](2.5/stretch/nodejs) - [2.5 full](2.5/stretch/full)
- [2.4 base](2.4/stretch) - [2.4 with nodejs](2.4/stretch/nodejs) - [2.4 full](2.4/stretch/full)

## Base version

Compiled ruby on Debian stretch with [jemalloc](http://jemalloc.net/) support.

## NodeJS version

Use ruby base image with [NodeJS 16.x](https://nodejs.org/en/) - [Yarn](https://yarnpkg.com/) - [MJML](https://mjml.io/)

## Full version

Use ruby with nodejs and add support to:

- Imagemagick
- MariaDB, MySQL or AuroraDB
- Common compiler binaries (GCC, C++, Make ...)

Prepare image to receive application in folder `/app`

## Example

Use this example to run Rails in docker Ruby full version

```dockerfile
FROM alboom/ruby-k8s-production:3.1-stretch-full

ENV BUNDLE_VERSION 1.16.0

RUN set -eux; \
    gem install -N bundler:${BUNDLE_VERSION}; \
    bundle config set without 'development test'

ADD Gemfile* $APP_HOME/
RUN bundle install

ADD . $APP_HOME

ENV PORT=3000 \
    RAILS_ENV=production \
    RAILS_LOG_TO_STDOUT=true

EXPOSE 3000
```

## Contribute

Use `.template` files to edit all Dockerfile versions.

Use `./scripts/update-ruby` to update images to latest versions and applying templates.

The build was executed with Github Actions. The workflow is generated automatically with `update-ruby` command too.
