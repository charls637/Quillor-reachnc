# reach
EducationNC Reach website 

SAGE STEPS (stable version 8) because the version 9 is still under development if we will use the v9 then we will follow the github steps then it uses yarn:

## INSTALLATION
Before starting make sure you have [Composer](https://getcomposer.org/download/) installed

### Open terminal and go/point it to your wordpress theme directory,  replace `your-theme-name` with the name of your theme, 8.5.1 is the latest stable version of sage	

```shell
c> cd wamp/www/site/wp-content/themes/ 
themes> composer create-project roots/sage your-theme-name 8.5.1
```

### Installing project dependencies
1. Install the latest Node.js
2. After installing Node.js, we recommend that you update to the latest version of npm and other dependencies. Install the latest npm, gulp and bower

```shell
c> npm install -g npm@latest
c> npm install -g gulp bower
your-theme-name> npm install 
your-theme-name> bower install
```

the first two command is for global command.

### To add a custom nav
1. From your theme folder navigate to `lib/setup.php` and add your custom navigation below this line 
`Register wp_nav_menu() menus`
2. Then to display it add this file on `header/footer or any page with this code`. Where as the `name_navigation` is the name of your custom nav.
`wp_nav_menu(['theme_location' => 'name_navigation', 'menu_class' => 'nav']);`
3. then go to terminal/cli and from your theme path write this command:
`your-theme-name> gulp`
4. that command means to Compile and optimize the files in your assets directory.

### To add a custom sidebar
1. From your theme folder navigate to `lib/setup.php` and add your custom navigation below this line (Register sidebars).
2. You can just duplicate and rename/duplicate the default sidebars.
3. Then navigate to `themes/templates` add your new file to display the custom side bar i.e. my-sidebar.php OR You can directly inject the sidebar to any file i.e. footer.php/header.php.
4. then just paste this code `<?php dynamic_sidebar('your-side-bar-id-name'); ?> `
5. then go to terminal/cli and from your theme path write this command:`your-theme-name> gulp`
6. that command means to Compile and optimize the files in your assets directory.

### To add a custom post type. (I created this by myself so just copy and paste the default options/data)
1. From your theme folder navigate to `functions.php` and add this value under the $sage_includes `lib/custom-post-types.php`
means that all your custom post type code will be coded on that file.
2. Navigate to `lib/custom-post-types.php` if you don't have that file then please create that file.
3. In this file make sure you call first this code `namespace Roots\Sage\CPT;` for sage functions.
4. then below that you can now register your new post types, taxonomies, rewrite rules and other functions.
5. I did make a sample so you can just copy and paste it.

### From here, you can customize your theme.. all of this steps can be found here https://roots.io/sage/docs/theme-installation/


*hint:
- everytime you add new code/css/style and want to view the result you must call the `gulp` command in the terminal to compile  your codes.

### Available gulp commands

* `gulp` — Compile and optimize the files in your assets directory
* `gulp watch` — Compile assets when file changes are made
* `gulp --production` — Compile assets for production (no source maps).


### Using BrowserSync

To use BrowserSync during `gulp watch` you need to update `devUrl` at the bottom of `assets/manifest.json` to reflect your local development hostname.

For example, if your local development URL is `http://project-name.dev` you would update the file to read:
```json
...
"config": {
"devUrl": "http://project-name.dev"
}
...
```
If your local development URL looks like `http://localhost:8888/project-name/` you would update the file to read:
```json
...
"config": {
"devUrl": "http://localhost:8888/project-name/"
}
...
```