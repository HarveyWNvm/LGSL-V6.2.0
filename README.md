# LGSL-V6.2.0
# Hello and welcome to LGSL Wiki!
### Visit for the first time? > Leave the Star and Fork LGSL Repo!
[![GitHub followers](https://img.shields.io/github/followers/tltneon?style=for-the-badge)](https://github.com/tltneon?tab=followers) [![GitHub stars](https://img.shields.io/github/stars/tltneon/lgsl?style=for-the-badge)](https://github.com/tltneon/lgsl/stargazers) [![GitHub forks](https://img.shields.io/github/forks/tltneon/lgsl?style=for-the-badge)](https://github.com/tltneon/lgsl/fork)
### Requirements
![PHP](https://img.shields.io/badge/PHP-5.4--8.x-brightgreen?style=for-the-badge&logo=php)
![MySQL](https://img.shields.io/badge/MySQL-5.5.27--8.0.x-brightgreen?style=for-the-badge&logo=mysql) or
![MariaDB](https://img.shields.io/badge/MariaDB-5.5--10.5.x-brightgreen?style=for-the-badge&logo=mariadb)

# Main links
### [Guide: How to install LGSL (standalone)](https://github.com/tltneon/lgsl/wiki/How-to-install-LGSL)
### [Guide: Make custom style](https://github.com/tltneon/lgsl/wiki/How-to-Make-own-style)
### [Help us: Translate LGSL](https://github.com/tltneon/lgsl/wiki#how-do-i-change-language)
### [Leave the feedback](https://docs.google.com/forms/d/e/1FAIpQLScx9zlMNvjpR3xUE-OZSttdGRojmncMU037LOk-c9mYIFYBdQ/viewform)
### [Donate on Patreon!](https://www.patreon.com/ru_neon)

[![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/tltneon/lgsl?style=for-the-badge)](https://github.com/tltneon/lgsl/archive/master.zip)
[![Packagist](https://img.shields.io/packagist/l/tltneon/lgsl?style=for-the-badge)](https://github.com/tltneon/lgsl/blob/master/LICENSE)

# FAQ
## Fast start? (using LGSL as PHP library)
1. [Download ZIP]([https://github.com/tltneon/lgsl/archive/master.zip](https://github.com/HarveyWNvm/LGSL-V6.2.0)) and extract or download via Composer: `composer require tltneon/lgsl`
2. Include `lgsl_class.php` and query data from server using `lgsl_query_live(protocol, ip, connect_port, query_port, software_port, flags)` function, where:
**protocol** - _server query protocol_, **ip** - _your server ip_, **connect_port** - _server connection port_, **query_port** - _server query port_, **software_port** - _server software port (mostly equal to 0)_, **flags** - _"s" for main info, "e" for extra data and settings, "p" for players data_.<br /><br />
**Example of using LGSL:**<br />
```php
<?php
  include('lgsl/lgsl_files/lgsl_class.php');
  $result = lgsl_query_live('urbanterror', '176.9.28.206', 27971, 27971, 0, "sep");
  print_r($result); // there is will be an array of result of querying
?>
```
## How to upgrade LGSL?
1. Download [stable version](https://github.com/tltneon/lgsl/releases) or [latest commit](https://github.com/tltneon/lgsl/archive/master.zip). _(*Note that commit can have any bugs)_
2. Backup your LGSL.
3. Extract new LGSL into your LGSL folder with replacing (**DO NOT replace lgsl_config.php**)<br />
3.1 Check out your **lgsl_config.php** and new one - there are can be several changes.
4. If everything is good - now you have most latest version of LGSL.
* In other cases just roll back to your backup version.
## How to go to Admin panel?
There are two ways you can enter the Admin panel: _(Note that you need to install LGSL first)_
1. Just typing http://*your_website*/lgsl_folder/admin.php (For example: http://*your_website*/lgsl/admin.php)
2. Clicking on the top right corner of the page. Cheers, you just found a hidden link, ha-ha.
## How to add servers to website's sidebar?
1. Set zone option to 1 at servers you need to show (at admin panel)
2. Add code to your website:
```php
<?php
  $lgsl_zone_number = 1;
  $output = "";
  require "lgsl/lgsl_files/lgsl_zone.php"; // note: you need to check route to that file!
  echo $output;
?> 
```
## How to make backup?
1. Open http://*your_website*/lgsl_files/lgsl_export.php
2. Copy whereever you need and save.

Possible parameters:
* Print as JSON: http://*your_website*/lgsl_files/lgsl_export.php?json=1
* Print as XML: http://*your_website*/lgsl_files/lgsl_export.php?xml=1
* Download as txt file: http://*your_website*/lgsl_files/lgsl_export.php?download=1
* Only online: http://*your_website*/lgsl_files/lgsl_export.php?online=1
* Only enabled: http://*your_website*/lgsl_files/lgsl_export.php?nodisabled=1
* Sorting by ip or type: http://*your_website*/lgsl_files/lgsl_export.php?sort=ip

For example, you can export enabled servers sorted by type as xml: http://*your_website*/lgsl/lgsl_files/lgsl_export.php?xml=1&nodisabled=1&sort=type

## Page loads slowly
 If you have more than 20 servers in your list, and you need the server information to be
 more accurate as to current players and map information, then you can schedule updates.

 Since LGSL updates when viewed, there has to be a limit on the update time otherwise the
 page would take a long time to load while it polls all the servers.

 By scheduling the webserver to 'view' LGSL at regular intervals, the server information
 is cached ready for when a visitor views LGSL.  Scheduling on webservers is known as a 'cron job'.

 Setting up a cron differs between hosts, so you may need find out what method your host supports,
 but here are examples of cron commands that I have used in the past.

 `curl --compressed -s -o /dev/null http://*your_website*/lgsl/lgsl_files/lgsl_cron.php`<br />
 `wget -q -O /dev/null http://*your_website*/lgsl/lgsl_files/lgsl_cron.php`<br />
 `php -q /public_html/lgsl/lgsl_files/lgsl_cron.php`<br />

 Before setting up the cron, its recommended that you view the lgsl_cron.php in your browser to
 make sure that there are no errors, and you can see how long it takes to update the servers.

## The icons and other images are not showing

  First make sure the icons uploaded properly and that you can directly open them in your browser.
  If LGSL is looking for them in the wrong place, manually set the path to /lgsl_files/ in
  the LGSL_CONFIG.php remembering to include the trailing slash, for example:

  $lgsl_config['url_path'] = "http://*your_website*/folder/gameservers/lgsl_files/";

# Troubleshooting with adding game server
## There is no game that I want to add!
Note that most of games builded on similar query protocols so they are grouped. Note that most of games builded on similar query protocols so they are grouped. To choose right game type, go to: https://github.com/tltneon/lgsl/wiki/Supported-Games,-Query-protocols,-Default-ports
## My server won't working!!
Before you say that LGSL isn't works:
1. Make sure your web hosting has open ports and allow to sending requests to game servers.
1. Make sure you're entered right connection port and query port.
1. Make sure your server is working now and also server's ports is opened.
1. For some servers uses slightly different query port than connection port. Try to enter query port as "**connection port + 1**". For example: Connection port 27015, so you trying to enter Query port 27016. That often meets with Killing floor, Unturned and some other servers. Also check [that page](https://github.com/tltneon/lgsl/wiki/Supported-Games,-Query-protocols,-Default-ports).

# Changing visuals
## How do I change style?
* Go to **lgsl_config.php**
* Find _**$lgsl_config['style'] = "breeze_style.css";**_ and replace at _**$lgsl_config['style'] = "darken_style.css";**_ for example.

You can find styles at **[/lgsl_files/styles/](https://github.com/tltneon/lgsl/tree/master/lgsl_files/styles)** folder.

## How do I change language?
* Go to **lgsl_config.php**
* Find _****include("languages/english.php");****_ at very end of file and replace at _**include("languages/russian.php");**_ for example.

You can find languages at **[/lgsl_files/languages/](https://github.com/tltneon/lgsl/tree/master/lgsl_files/languages)** folder.

And a few lines at file **[install.php](https://github.com/tltneon/lgsl/blob/master/install.php#L310)**

Can't find your language? [Contribute](https://github.com/tltneon/lgsl/pulls) us your translation with your native language!

(_You can use [Google Translate](https://translate.google.com/) if you need_)
## How can I make my own style?
You **need to know [CSS3](https://developer.mozilla.org/en-US/docs/Web/CSS)** and use Developer Tools (e.g. [DevTools](https://developer.mozilla.org/en-US/docs/Tools/Style_Editor) into Mozilla Firefox).

* Make file ***your_file_name*.css** at **/lgsl_files/styles/** folder.
* Change style in **lgsl_config.php** and now you have your own custom style of LGSL!

## How can I add map images?
* All of map images stores at /lgsl_files/maps/
* Images should be only **.png**, **.gif**, **.jpg**
* Since LGSL v5.10.2 you can add images with various resolutions (but keep in mind that can affects on page loading speed) 

For example, we have any CS:GO server with map de_dust2. So to add map image we need to look at game type, game name and map name. CS:GO has gametype "**source**", game name "**csgo**" and map name "**de_dust2**". After we get that we can upload map image called de_dust2.jpg into /lgsl_files/maps/**source**/**csgo**/ folder. If it isn't exists - just create! That's all! If you correctly made it default map image will be replaced with yours new.
[Watch in YouTube](https://www.youtube.com/watch?v=3u30DyWpSh8)

Most common images you can download from [here](https://www.dropbox.com/s/0zzbybp8cokngs6/lgsl_map_images_standard.zip?dl=0).


## How can I help with .. ?
Mainly we need to help with finding bugs and to help to translate to any language.<br />
Any your ideas (such as new style, game type, new feature) you can suggest to [Issues](https://github.com/tltneon/lgsl/issues) page.<br />
Also you can fork LGSL repository and give a star. Thanks!
