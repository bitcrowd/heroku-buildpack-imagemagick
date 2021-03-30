heroku-buildpack-imagemagick
=================================

🚨 This repository is archived and will not receive maintenance from us anymore.

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for vendoring the ImageMagick binaries into your project. It was forked from [this repo](https://github.com/ello/heroku-buildpack-imagemagick).

## How it works
Rather than pulling down binary dependencies from a package manager and extracting them into place, this buildpack compiles Imagemagick from source the first time an app is built with it. The compiled binaries are cached for future builds, so this penalty is only incurred once.

This has the downside of a (potentially very long) deploy time for the first push, with the benefit of a less-fragile build product that's somewhat less likely to break due to platform and dependency shifts. Or at least, that's the hope!

## Stack compatibility
This buildpack is tested primarily against the `cedar-14` stack. Currently, a workaround is required to make it work on the newer `heroku-16` stack - see https://github.com/ello/heroku-buildpack-imagemagick/pull/17 for details.


## Details
- This buildpack installs ImageMagick version `7.0.10-56`
- This buildpack **enables** `HTTPS`, which allows to fetch images from a (trusted) third-party.

## Warning

:rotating_light: **Do not use this buildpack if you do not need to enable `HTTPS` as a policy.** :rotating_light:

See:
- https://devcenter.heroku.com/changelog-items/891
- https://github.com/ImageMagick/ImageMagick/issues/1342
- https://github.com/ImageMagick/ImageMagick/blob/master/config/policy.xml

