# wp shell utils

This repository contains a collection of shell utilities I wrote for WordPress. They require a Bash-compatible shell and the presence of [WP CLI](http://wp-cli.org).

Manifest:

+ `bash.lib`. This file contains variable definitions for programs and a few other settings. Most of the programs source this file. Review the variables at the bottom of the file to customize it for your environment.
+ `wp-make-site`. This script downloads and installs a new WordPress instance. Since I use [Laravel Valet](https://laravel.com/docs/10.x/valet), the program creates a new secure link. [1Password CLI](https://developer.1password.com/docs/cli/) is also called to store temporary credentials. **Note:** change the email address variable `$ADMIN_EMAIL`.
+ `wp-remote-copy`. This script makes a backup of a WP instance on a remote server, copies the `*.wpress` file to the localhost, and restores it to a local WP instance. **Note:** the script has two additional requirements:
  + The freely available [All-in-One WP Migration](https://wordpress.org/plugins/all-in-one-wp-migration/) plugin.
  + A commercial extension to the above plugin, such as [the Multisite Extension](https://servmask.com/products/multisite-extension) (or another extension that provides [WP CLI](http://wp-cli.org) support).
+ `wp-sync-site`. This script creates a backup of one site and restores it to a second site. It's basically a quick way to duplicate a site on the localhost. **Note:** WordPress must be installed on the destination site. 
  + The freely available [All-in-One WP Migration](https://wordpress.org/plugins/all-in-one-wp-migration/) plugin.
  + A commercial extension to the above plugin, such as [the Multisite Extension](https://servmask.com/products/multisite-extension) (or another extension that provides [WP CLI](http://wp-cli.org) support).
+ `wp-rename-theme`. Ever needed to rename the directory of a theme? This script will rename a folder and update the database accordingly.
+ `wp-rename-plugin`. Ever needed to rename the directory of a plugin? This script will rename a folder and update the database accordingly.
+ `wp-reset-admin-user`. This script resets the admin username (including the user_login), password, and email. **Note:** change the email address variable `$NEW_EMAIL`.
+ `wp-delete-all-posts`. This script deletes all posts of a given post type.
+ `wp-update-core`. This script backs up and updates the WordPress core files of several sites in a given directory. This script has three additional requirements:
  + The freely available [All-in-One WP Migration](https://wordpress.org/plugins/all-in-one-wp-migration/) plugin.
  + A commercial extension to the above plugin, such as [the Multisite Extension](https://servmask.com/products/multisite-extension) (or another extension that provides [WP CLI](http://wp-cli.org) support).
  + The $WEBSITES_DIR variable needs to be defined.
+ `wp-sync-uploads`. This script uses `rsync` to sync the `/wp-content/uploads` folder between a remote WP instance and a local one. (New items on the server are copied to the localhost.) **Note:** this script requires [WP CLI aliases](https://make.wordpress.org/cli/handbook/guides/running-commands-remotely/) on the localhost to have the "path" property set.