A simple initial configuration for Planet GitHub (a collection of GitHub employee blogs aggregated together), using Planet Venus as the provider. This is not designed to be a big, official GitHub service, just a place to conveniently read what is going on.

Instructions
============

Initial setup:

1. mkdir planetgithub
2. cd planetgithub
3. git clone https://github.com/rubys/venus.git
4. git clone https://github.com/jonobacon/planetgithub

Possible extra stuff

1. sudo apt-get install xsltproc

Building the pages

1. cd planetgithub
2. python ../venus/planet.py githubio.ini
3. firefox html/index.html

(Once happy that this works, stick "`cd /path/to/planetgithub/planetgithub && python ../venus/planet.py githubio.ini`" in cron hourly or something.)

Adding new blogs is a question of editing planetgithub/planetgithub/githubio.ini and adding a new section which looks like

    [http://url/for/website/feed]
    name = Site Owner's Name

Note that you can't put the URL of the website *itself* in; it has to be the URL for the feed. You can inspect the site for the feed URL, or use https://pypi.python.org/pypi/feedfinder or similar tools.

Edit planetgithub/planetgithub/templates/githubio/index.html.tmpl to change the look of the site. Note that while changing the templates, you can run `python ../venus/planet.py -o githubio.ini` (note the `-o`) which will regenerate the site from the cache without hitting the network, which is a lot faster.
