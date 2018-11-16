The Nginx config is located at /etc/nginx/sites-enabled/default.
LetsEncrypt is configured and I added a crontab entry to check for renewal
daily.

The project folder is located at /srv/shyfts.

I followed the instructions located at
https://github.com/sharetribe/sharetribe#setting-up-sharetribe-for-product ion​ to set up the DB etc.
The database config is a copied version of
/srv/shyfts/config/database.example.yml to /srv/shyfts/config/database.yml
and just contains all the DB info I made when installing mysql.

The config (with API keys etc) is located at
/srv/shyfts/config/config.yml. Note that the smtp_email_port is 2525 and
not the typical 587. This is to solve the email sending issue. The rest of
the smtp_email_* details are from SendGrid.

There are 3 SystemD files located within /etc/systemd/system called
sharetribe{1,2,3}.service. These run the web server and background tasks.
To restart these, run `systemctl restart sharetribe{1,2,3}`.

I had to manually set the domain by following https://github.com/sharetribe/sharetribe#setting-your-domain​. Type `mysql -p` and enter the DB password. Select the DB by `use sharetribe_production;`. Then you can set the values. I ran `update communities set domain=’shyfts.io’;` and `update communities set use_domain=1;`.