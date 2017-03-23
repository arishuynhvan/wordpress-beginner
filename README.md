
     ,-----.,--.                  ,--. ,---.   ,--.,------.  ,------.
    '  .--./|  | ,---. ,--.,--. ,-|  || o   \  |  ||  .-.  \ |  .---'
    |  |    |  || .-. ||  ||  |' .-. |`..'  |  |  ||  |  \  :|  `--, 
    '  '--'\|  |' '-' ''  ''  '\ `-' | .'  /   |  ||  '--'  /|  `---.
     `-----'`--' `---'  `----'  `---'  `--'    `--'`-------' `------'
    ----------------------------------------------------------------- 


Welcome to your WordPress website on Cloud9 IDE!

To get you started, we've already...

1) Started MySQL using:

   $ mysql-ctl start

2) Clicked the Run Project button

3) Clicked on Preview > Preview Running Application

And now you are ready to configure your WordPress admin interface!

Happy coding!
The Cloud9 IDE team


## Support & Documentation

Visit http://docs.c9.io for support, or to learn more about using Cloud9 IDE. 
To watch some training videos, visit http://www.youtube.com/user/c9ide

## Archive entire site

This is not only applicable to wordpress

```
wget --mirror -p --html-extension --convert-links -e robots=off -P . http://url-to-site
```

That command doesn’t throttle the requests, so it could cause problems if the server has high load. Here’s what that line does:

* --mirror: turns on recursion etc… rather than just downloading the single file at the root of the URL, it’ll now suck down the entire site.
* -p: download all prerequisites (supporting media etc…) rather than just the html
* --html-extension: this adds .html after the downloaded filename, to make sure it plays nicely on whatever system you’re going to view the archive on
* --convert-links: rewrite the URLs in the downloaded html files, to point to the downloaded files rather than to the live site. this makes it nice and portable, with everything living in a self-contained directory.
* -e robots=off: executes the “robots off” command, telling wget to ignore any directive to ignore the site in question. This is strictly Not a Good Thing To Do, but if you own the site, this is OK. If you don’t own the site being archived, you should obey all robots.txt files or you’ll be a Very Bad Person.
* -P .: set the download directory to something. I left it at the default “.” (which means “here”) but this is where you could pass in a directory path to tell wget to save the archived site. Handy, if you’re doing this on a regular basis (say, as a cron job or something…)
* http://url-to-site: this is the full URL of the site to download. You’ll likely want to change this.

You may also need to play around with the -D domain-list and/or --exclude-domains options, if you just want to control how it handles content hosted on more than one domain.

It’s worth noting that this isn’t WordPress-specific. This should work fine for archiving any website.

Source: [darcynorman.net](https://darcynorman.net/2011/12/24/archiving-a-wordpress-website-with-wget/)

Alternative (which I used and it seems to work)

```
wget –html-extension –convert-links -m -w 20 http://example.com
```

The different flag:

* -w 20 – This command puts 20 seconds in between each file retrieved so it doesn’t hammer the server with traffic.


Source: [wptavern.com](https://wptavern.com/how-to-archive-a-site-you-dont-have-access-to)