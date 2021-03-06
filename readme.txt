=== Plugin Name ===
Contributors: mabujo
Donate link: http://plusdevs.com/donate
Tags: google+, widget, sidebar, google, social, google plus, +1, google +, google +1, stats
Requires at least: 3
Tested up to: 3.2
Stable tag: trunk,

A simple plugin that adds a google+ widget for linking to your google+ profile and showing your number of followers

== Description ==

googleCards is a google+ wordpress plugin.
It adds a widget to your blog that will display a link to your google+ profile so people can add you to a circle (follow you). It also displays your name, profile picture and the number of people who have you in circles.

The plugin uses caching to store your google plus profile data to eliminate checking google+ on every page load.
For the caching to work, your web-server needs to be able to write to wp-content. (a lot of plugins require this so it should be fine).
If the plugin cannot cache it will still work, but will store the data in the database instead. If caching is working you should see a file called plus_card.txt in /wp-content/cache/.
As of version 0.4, caching will also failback to using transients to store your scraped google plus data.

Plugin page : [Google plus wordpress plugin @ plusdevs](http://plusdevs.com/google-wordpress-plugin/)

== Installation ==

1. Download googleCards.zip and unzip
2. Upload the unzipped googleCards folder to the `/wp-content/plugins/` directory
3. Activate the plugin through the 'Plugins' menu in WordPress
4. Go to the 'Widgets' menu in Wordpress and add the widget to your sidebar.
5. Choose a title for the widget and input your google+ id. (You can find your google+ id by going to your profile, it is the 21 digit number e.g. plus.google.com/YOUR_ID_IS_HERE).

== Frequently Asked Questions ==

= I get the error “Parse error: syntax error, unexpected T_STRING, expecting T_OLD_FUNCTION or T_FUNCTION or T_VAR or ‘}’ in plugins/googlecards/googleCardClass.php on line 25“ =

This is a problem with your PHP setup. You are almost certainly running PHP4. The plugin requires PHP5. WordPress requires PHP5 after version 3.2 too. Talk to your host about using PHP5.

= I get the error “Warning: file_get_contents() [function.file-get-contents]: Filename cannot be empty in /*****/*****/public_html/blog/wp-content/plugins/googlecards/googleCardClass.php on line 181“ =

You probably have something other than your Google+ id in the Google+ id box. Make sure you just put in the numbers from the url of your Google+ profile and nothing else.

= I get the error “Warning: file_get_contents(http://plus.google.com/*******… [function.file-get-contents]: failed to open stream: HTTP request failed! HTTP/1.0 403 Forbidden“ =

This is a HTTP 403 error from Google+, it means they have banned your server’s IP from making requests to their servers. This usually isn’t anything to do with the plugin (it makes very few calls to Google’s servers) and it is more likely that you are on shared hosting, and someone else who shares your IP has been scraping Google.

= I get the error “file_get_contents(http://plus.google.com/… [function.file-get-contents]: failed to open stream: Unable to find the socket transport “ssl” – did you forget to enable it when you configured PHP?“ =

Because Google+ is HTTPS, you need to get your host to enable openssl and configure it for PHP.

= I get the error “Warning: file_get_contents() [function.file-get-contents]: URL file-access is disabled in the server configuration in /var/www/web1281/html/wordpress/wp-content/plugins/googlecards/googleCardClass.php on line 181“. AND/OR I get the error “Warning: file_get_contents(http://plus.google.com/1082378… [function.file-get-contents]: failed to open stream: no suitable wrapper could be found in /var/www/web1281/html/wordpress/wp-content/plugins/googlecards/googleCardClass.php on line 181“ =

The plugin requires either CURL or file_get_contents() to be enabled on your server.If your host gives you access to your php.ini then you can change the ‘allow_url_fopen’ setting to ’1′ which will fix your problem. Otherwise speak to your host and ask them to enable CURL or allow_url_fopen for you.

== Screenshots ==

1. googleCards widget in the sidebar

== Changelog ==
= 0.4.7 =
* Fixing the class names once again after a google+ change.

= 0.4.6 =
* Another fix for profile picture and circle count failing after google changed the plus profiles...

= 0.4.5 =
* This update fixes fetching of the circle count and the profile picture - it broke when Google changed the class names of the containing elements.

= 0.4.4 =
* Added option for adding rel=author to profile links, and an option to open profile links in a new tab.

= 0.4.3 =
* Added contribution from Joe Vaughan for using the Wordpress 3.0 widget API so widget can be used in multiple sidebars. Thanks Joe, chapeau. Also added the option to disable the developer credit if you're a really mean sort of person and removed the example Google+ ID.

= 0.4.2 =
* Forever alone - fix for bug when no one has the google+ account in a circle.

= 0.4.1 =
* Test for safe_mode and open_basedir. Fixes curl_setopt() bug.

= 0.4 =
* Added file_get_contents as a backup for curl and use the transients API if we cant use a cache file. Tell curl not to verify https. Some minor css stuff.

= 0.3.1 =
* Some css fixes for people with big names and small sidebars.

= 0.3 =
* Fix for lowercase names in wordpress plugin directory

= 0.2 =
* Fixed some caching and css problems

= 0.1 =
* Initial release

== Upgrade Notice ==
= 0.4.5 =
* This plugin stopped being able to fetch the profile image and circle count when Google changed elements of Google+ profiles. This update fixes the problem.

= 0.4 =
googleCards no longer requires a cache file to work and should be much more reliable in fetching your data from google+. If you were having problems before please upgrade and try this new version.