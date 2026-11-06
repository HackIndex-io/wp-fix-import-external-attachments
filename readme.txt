=== Import external attachments (HackIndex Patched) ===
Contributors: ryanpcmcquen, joshuavanderpoll
Donate link: https://ryanpcmcquen.org
Tags: images, gallery, photobloggers, attachments, photo, links, external, photographers, Flickr, save, download, pdf
Requires at least: 3.2
Tested up to: 7.1
Stable tag: 1.5.13
License: GPLv2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html

Makes local copies of all the linked images and pdfs in a post, adding them as gallery attachments. (HackIndex Patched)

== Description ==

= HackIndex Patched fork =
This is an unofficial fork of Import external attachments by Ryan P.C. McQuen. The original plugin is no longer maintained and its latest release (1.5.12) has known vulnerabilities ([CVE-2025-64245](https://www.wordfence.com/threat-intel/vulnerabilities/id/25ff4093-f8bf-41f8-b9d8-c15ecee71b43), [CVE-2025-53268](https://www.wordfence.com/threat-intel/vulnerabilities/id/2c4faf5b-70bf-4682-89bb-aa3fc19b29e8)). HackIndex maintains this fork for security fixes only.

* We fix security issues and keep the plugin working on current WordPress and PHP versions. We do not add features or change how the plugin works.
* It is a drop-in replacement: same plugin folder and settings, so your excluded domains and imported attachments are kept.
* HackIndex is not affiliated with or endorsed by Ryan P.C. McQuen. Please do not contact the original author for support with this fork, open an issue on the fork instead.
* Original plugin: [WordPress.org](https://wordpress.org/plugins/import-external-attachments/) and [GitHub](https://github.com/ryanpcmcquen/import-external-attachments) by Ryan P.C. McQuen.
* HackIndex fork and issues: [github.com/HackIndex-io/import-external-attachments](https://github.com/HackIndex-io/import-external-attachments)
* Licensed under the GPLv2 or later, like the WordPress.org release, and provided without any warranty.

Makes local copies of all the linked images and pdfs in a post, adding them as gallery attachments.

Source & support:

https://github.com/ryanpcmcquen/import-external-attachments

= Credits =

This plugin is based on the work done in the "Import External Images" plugin by MartyThornley.

https://github.com/MartyThornley

HTTPS support added by IvanDoomer:
https://github.com/IvanDoomer

PDF support added by bengreeley:
https://github.com/bengreeley

Most of the JavaScript was rewritten from the original plugin, to reduce the
number of global variables.

== Installation ==

1. Download the "Import external attachments" zip file.
2. Extract the files to your WordPress plugins directory.
3. Activate the plugin via the WordPress Plugins tab.

== Frequently Asked Questions ==

= How does this plugin work? =

The plugin examines the HTML source of your post when you save it, inspecting each IMG tag, and processing them according to the options you have selected.

Under the default settings, it will find IMG tags with links to images on other web sites and copy those images to your web site, updating the IMG src to point to your copy.

PDF functionality was added by bengreeley.

= Does it work with MultiSite? =

Yes! It was developed and built (and is used everyday) at PhotographyBlogSites.com - a multisite install.

= What if i don't want to import images from a third party image hosting site? =

You can make it ignore any domain you want on the settings page, in case you work with a CDN or photo hosting site and want to keep those images where they are.

== Changelog ==

= 1.5.13 =

* Security: fixed Missing Authorization ([CVE-2025-64245](https://www.cve.org/CVERecord?id=CVE-2025-64245), [Wordfence advisory](https://www.wordfence.com/threat-intel/vulnerabilities/id/25ff4093-f8bf-41f8-b9d8-c15ecee71b43)) that let any logged in user, including subscribers, import the external files of any post and rewrite its content, and list the posts with external files. Both AJAX actions now require the `edit_theme_options` capability of the Import attachments page and a nonce.
* Security: fixed Cross-Site Request Forgery ([CVE-2025-53268](https://www.cve.org/CVERecord?id=CVE-2025-53268), [Wordfence advisory](https://www.wordfence.com/threat-intel/vulnerabilities/id/2c4faf5b-70bf-4682-89bb-aa3fc19b29e8)) on the Import attachments page, where a link could change the settings or start the import of all posts. Saving settings and processing all posts now verify the nonce.
* Security: escaped post titles in the import results and the list of posts, and the file URLs in the post edit box
* Fixed PHP warnings on PHP 8
* Tested with WordPress 7.1 and PHP 8.0 to 8.5

= 1.5.12 =

* Adds support for pages.
* Adds support for `.doc` and `.docx` files.
* Fixes security issue by not directly echoing `$_GET['post']` but casting it to `int`.
* Adds support for filenames with spaces in them (by removing the space from the exclusion in the regex).
* Makes the regexes slightly easier to read by making them case insensitive.

= 1.5.11 =

Add .jpeg support.

= 1.5.9 =

Remove duplicate README.

= 1.5.8 =

Fix some typos.

= 1.5.7 =

Add GitHub link.

= 1.5.6 =

Fix naming.

= 1.5.5 =

Make import_images_start_time a function. Hopefully it works now.  :^)

= 1.5.4 =

Make import_images_start_time globally accessible.

= 1.5.3 =

General cleanup.

= 1.5.1 =

Merged upstream pull requests from bengreeley and IvanDoomer and changed to 'Import external attachments'.
Now supports PDFs and HTTPS!

= 1.3 =

Fixed case sensitivity, thanks to https://github.com/SidFerreira
Fixed duplicate EXTERNAL_IMAGES_DIR notice

= 1.1 =

Fixed title in readme.
