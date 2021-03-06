[![Build Status](https://api.travis-ci.org/modess/git-pretty-stats.png)](https://api.travis-ci.org/modess/git-pretty-stats.png)

You know those cool graphs and statistics you can get for a repository on github? The things is that (unfortunately) not all git repositories are hosted on github for various reasons. This is the tool for rendering graphs for your repository that can be hosted anywhere, and it looks great.

## Features

* Handles multiple repositories
* Handles bare repositories
* Statistics
  - Total commits
  - Total contributors
  - Average commits per contributor
  - First commit date
  - Latest commit date
  - Active for (X days)
  - Average commits per day
* Graphs
  - Commits by date
  - Commits by hour of day
  - Commits by day of week
  - Commits by contributor

## Requirements

* PHP >= 5.3
* Git

## Installation

Start by clone this repository and setup your web server. Take a look at the great repository [laravel-website-configs](https://github.com/daylerees/laravel-website-configs) by Dayle Rees for Laravel web server configurations.

Install dependencies using [Composer](http://getcomposer.org/)

    php composer.phar install

You also need to set permission to the applications storage folder

    chmod -R 777 app/storage

Clone the repositories you want to statistics and graphs for in to the **repositories** folder.
```php
cd repositories
git clone <repository-url>
```
You can clone as many as you want to in to this folder.

### Configuration
To manually override configuration, start by copying `app/config/git-pretty-stats.php` to `app/config/local/git-pretty-stats.php`. Then you can configure the following in that file:

**Custom directory for repositories**

Set the `repositoriesPath` to a relative path where you store your repositories
```php
'repositoriesPath' => '../../repositories'
```
**Specify each repository path**

Set the `repositoriesPath` to an array of paths. They can be either relative or absolute.
```php
'repositoriesPath' => array(
    '/var/www/web-project',
    '../test-project'
);
```

**E-mail aliases**

Sometimes a user will contribute using different e-mail addresses to a repository. If you want to you can manually map the aliases for this. To add commits to `user_new@email.com` made by `user_old@email.com` you can do this (you can add as many as you like):
```php
'emailAliases' => array(
    'user_old@email.com' => 'user_new@email.com'
);
```

***

Now go to your web browser and go to the URL where you've set everything up.

*Disclaimer: the tool has been tested to work on repositories up to 10 000 commits. If your repository have a higher number of commits than that you might experience issues.*

## Upgrade from 0.3 to 0.4

Since `0.4` the application is based on the Laravel framework and some changes have been made. All you need to do (except following the installation instructions again) is to move your `config.php` to `app/config/local/git-pretty-stats.php` if you have one.


## Contribute

1. Check for [open issues](https://github.com/modess/git-pretty-stats/issues) or open a fresh issue to start a discussion around a feature idea or a bug.
2. Fork the [git-pretty-stats](https://github.com/modess/git-pretty-stats) repository on Github to start making your changes.
3. Write test(s) which shows that the bug was fixed or that the feature works as expected.
5. Send a pull request to the **develop** branch. Make sure to add yourself to CONTRIBUTORS.md.

If there is some certain statistics or graph that you are missing and would like to be added? [Create an issue](https://github.com/modess/git-pretty-stats/issues/new) and request it!

## Screenshots

For more screenshots visit the [project homepage](http://www.codingswag.com/git-pretty-stats).

![](http://www.codingswag.com/wp-content/uploads/2013/06/Screenshot-2013-07-10-at-14.38.34.png)

![](http://www.codingswag.com/wp-content/uploads/2013/06/Screenshot-2013-07-10-at-14.38.43.png)

## Powered by

* [Laravel](https://github.com/laravel/laravel)
* [Gitter](https://github.com/klaussilveira/gitter)
* [Carbon](https://github.com/briannesbitt/Carbon)
* [Flat UI](https://github.com/designmodo/Flat-UI)
* [Highcharts JS](https://github.com/highslide-software/highcharts.com)
* [Handlebars.JS](https://github.com/wycats/handlebars.js)
* [Font Awesome](https://github.com/FortAwesome/Font-Awesome)

## TODO

* Cache for large repositories
* More graphs/statistics
* Additions / deletions for contributors

