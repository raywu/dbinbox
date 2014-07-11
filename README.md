Domokunphotos
=============

Domo Kun Photos is open source. This [software](https://github.com/raywu/domokunphotos) project is originally forked from [christiangenco/dbinbox](https://github.com/christiangenco/dbinbox). Share a link through Domo Kun Photos and crowdsource photos from your friends: http://domokunphotos.herokuapp.com/

Forked from dbinbox (README)
----------------------------

**Notice**: this branch is not longer the deployed branch in preparation for handling financial data for premium features on dbinbox.com. This public branch can now be simplified to support single instance deployments on Heroku (or another PaaS), and won't need to support more than a single account.

an inbox for your Dropbox. Try it out at [dbinbox.com](http://dbinbox.com)!

By visiting your personal dbinbox url, non-Dropbox users will be able to upload files straight into a special inbox folder in your Dropbox.

This is also quite handy if you need to send yourself a file from someone else's computer but don't want to log into email or remember a tinyurl.

An answer to https://forums.dropbox.com/topic.php?id=3525

Uses: https://github.com/blueimp/jQuery-File-Upload

And: http://datamapper.org/


Deploying a private instance
-----------------------------

### Heroku

To deploy on Heroku's Cedar stack:

1. Create a new app and add the heroku-postgresql addon:

        heroku apps:create
        heroku addons:add heroku-postgresql

2. Set BUNDLE_WITHOUT to ignore the sqlite dependencies (this requires
   enabling the user_env_compile feature flag):

        heroku labs:enable user-env-compile
        heroku config:set BUNDLE_WITHOUT="development:test:sqlite"

3. Configure your Dropbox key and secret

        heroku config:set DROPBOX_KEY="my-dropbox-key"
        heroku config:set DROPBOX_SECRET="my-dropbox-secret"

4. Set some Heroku-specific settings

        heroku config:set LOG_TO_STDOUT=true

5. Push!

        git push heroku master
