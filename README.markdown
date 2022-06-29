# Assets Preload Buildpack

A simple buildpack to run two scripts with the `$SOURCE_VERSION` as the one
parameter.

`bin/get_assets $SOURCE_VERSION`
`bin/extract_assets $SOURCE_VERSION`

## Rationale

Heroku runs `rake assets:precompile` as part of the rails buildpack. This is a
long process and can be redundant if you are building assets elsewhere, such as
during a build phase of your CI/CD pipeline.

How you might use this is have `get_assets` download a tarball from an S3 bucket
and then have `extract_assets` extract that tarball.

Doing this can greatly decrease deploy times. This is language and platform
agnostic. It was written for Rails, but you could load prebuilt assets for
anything here.

