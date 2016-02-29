---
inFeed: true
hasPage: true
inNav: false
inLanguage: null
starred: false
keywords: []
description: A summary of my workflow for local development that is release to Pantheon.
datePublished: '2016-02-29T21:46:09.761Z'
dateModified: '2016-02-29T21:45:48.106Z'
title: Drupal and Pantheon Local Workflow.
author: []
sourcePath: _posts/2016-01-29-important.md
published: true
authors: []
publisher:
  name: null
  domain: null
  url: null
  favicon: null
url: important/index.html
_type: Article

---
# Drupal and Pantheon Local Workflow.
![The Pantheon in Rome (Italy)](https://the-grid-user-content.s3-us-west-2.amazonaws.com/c62b00f9-5782-490e-8f13-c799c801b57f.jpg)

When I first started development with Drupal I spent a long time working out how to set up sites using [Aegir][0]. This worked well for me as my first site  was also hosted in production using Aegir, but on my second I ended up hosting with [Pantheon][1], and bended my workflow in ways that started to hurt. Now with that second project live, I took a step back and looked at my workflow and identified the pain points. 

They included:

* Static build and drupal build were disconnected.
* Drupal code I was developing againsts was different to what was running in production.
* The data I was developing againsts was different to what was running in production.

I decided on integrating my static build and Drupal workflow first this was easily achieved by extending my gulp build to know what to do with drupal files.

Next I installed Nginx, PHP-FPM and MariaDB. To set up a Site I took the following steps:

* Created a project in Pantheon and pulled this via git to my dev box.
* Created a git repository (in my case hosted with BitBucket) to house my custom work, also pulling it down to my dev box.
* Installed any extra modules with Git SubTrees. You can read more about how to do that [here][2].
* Create a symlink between the Pantheon repository and the www root. 
[How do I do this?][3]
* Create a new file in /etc/nginx/sites-available with the nave of your site. I have an example of this file [here][4].
* Enable the Site by linking this new file to /etc/nginx/sites-enabled/.
* Restart Nginx. If you receive any errors run "_nginx -t_", this will validate your configuration and will help pinpoint the issue.
* Now all is left is to add a hosts entry, this is done by editing  /etc/hosts and adding an entry for your new site.

Before we navigate to our site we need to do a bit of playing with the settings file.  

* Rename the settings.php to settings.php.backup.
* Create a new settings.php from the default.settings.php.
* Edit this file and remove everything before the comment starting with  "Include the Pantheon-specific settings file".
* Navigate to your site.

**It is worth noting that things are slightly different for Drupal 7 where you will just create a settings.php from the default.settings.php and continue. **

After navigating to your new site, you will be greeted with the install page, it is important to run through this, this will configure the settings.php with a local database connection string. Don't worry too much about what options you choose here as we will be overriding the database from a back up we get from the Pantheon dashboard.

**You will most likely run into a permissions issue here, open a shell and navigate to the pantheon repo and run "chmod a+w sites/default" this will set the permissions up correctly for you to continue.**

**IMPORTANT!!!**

Now that we have a working site it is **VERY IMPORTANT** to alter your settings.php so that it will work correctly when you commit all this back into the Pantheon repo.

* Change the name of the "**settings.php**" to "**settings.local.php**".
* Change the name of the "**settings.php.backup**" to "**setting.php".**

If you open up the now "settings.php" you will see that the "**settings.local.php**" will be favored over the "**settings.pantheon.php**" if it exists. Also have  alook at the "**.gitignore**" file in the root of your repo and you will see that the "**settings.local.php**" is ignored and will not be committed. 

Now we should have a working site, this is getting very long so I will call it there and pick up on the Build pipeline side of this another time.

[0]: http://www.aegirproject.org/
[1]: https://pantheon.io/
[2]: https://thegrid.ai/public-abstract-gravy-power/git-subtrees-and-modules/
[3]: null
[4]: https://gist.github.com/gravypower/f8bda2e9a1eea46bc664