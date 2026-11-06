# Import external attachments (HackIndex Patched)

> [!IMPORTANT]
> This is an unofficial fork of [Import external attachments](https://wordpress.org/plugins/import-external-attachments/) by [Ryan P.C. McQuen](https://github.com/ryanpcmcquen/import-external-attachments). HackIndex is not affiliated with or endorsed by the original author.

The original plugin is no longer maintained and its latest release (1.5.12) has known vulnerabilities ([CVE-2025-64245](https://www.wordfence.com/threat-intel/vulnerabilities/id/25ff4093-f8bf-41f8-b9d8-c15ecee71b43), [CVE-2025-53268](https://www.wordfence.com/threat-intel/vulnerabilities/id/2c4faf5b-70bf-4682-89bb-aa3fc19b29e8)). HackIndex maintains this fork for security fixes only:

- We fix security issues and keep the plugin working on current WordPress and PHP versions.
- We do not add features or change how the plugin works.
- It is a drop-in replacement: same plugin folder and option names, so your settings and imported attachments are kept.

Need help with this fork? [Open an issue](https://github.com/HackIndex-io/import-external-attachments/issues) here, please don't contact the original author about it.

This fork is based on the WordPress.org release 1.5.12, which is licensed under the GPLv2 or later. Later commits in the upstream repository switched to the MPL 2.0 but were never released.

## What it does

Finds images, PDFs and Word documents on other sites that are linked in your posts and pages, copies them to your media library and updates the links. Import per post with the "Import external media?" checkbox in the post edit screen, or for all posts under **Media > Import attachments**.

## Security fixes

### 1.5.13

- Missing Authorization ([CVE-2025-64245](https://www.cve.org/CVERecord?id=CVE-2025-64245), [Wordfence advisory](https://www.wordfence.com/threat-intel/vulnerabilities/id/25ff4093-f8bf-41f8-b9d8-c15ecee71b43)): the two AJAX actions behind "Import attachments now" had no capability check or nonce, so any logged in user, including subscribers, could import the external files of any post (rewriting its content) and list the posts with external files. They now require the `edit_theme_options` capability of the Import attachments page and a nonce.
- Cross-Site Request Forgery ([CVE-2025-53268](https://www.cve.org/CVERecord?id=CVE-2025-53268), [Wordfence advisory](https://www.wordfence.com/threat-intel/vulnerabilities/id/2c4faf5b-70bf-4682-89bb-aa3fc19b29e8)): the Import attachments page saved its settings and processed all posts without checking the nonce, so a page an administrator visited could do both. The nonce is now verified.
- Post titles in the import results and the list of posts, and the file URLs in the post edit box, are escaped
- Fixed PHP warnings on PHP 8
- Tested with WordPress 7.1 and PHP 8.0 to 8.5

## Install

1. Download `import-external-attachments.zip` from the [latest release](https://github.com/HackIndex-io/import-external-attachments/releases/latest).
2. Upload the zip in **Plugins > Add New > Upload Plugin** and choose **Replace current with uploaded**. Your settings are kept.
3. Don't delete the original plugin first: deleting a plugin can run its uninstall and remove its settings.

WordPress does not update this fork automatically. Watch this repo's releases to get new security fixes.

## License

GPLv2 or later, like the WordPress.org release. See [LICENSE](LICENSE). Provided without any warranty.

All credit for the plugin goes to [Ryan P.C. McQuen](https://github.com/ryanpcmcquen/import-external-attachments) and the authors it is based on (Marty Thornley, Randy Hunt). The full upstream history is kept in this repository.
