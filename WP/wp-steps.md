# Wordpress theme steps

---

- Create a style.css with the informations of the theme in comment

```css
/* 
    Theme Name: <NAME>
    Author: <AUTHOR>
    Description: <DESCRIPTION>
    Version: 1.0
*/
```

- Create a screenshot.png file in the main folder so the theme has a cover (1200px / 900px)

- Create the following files

     - index.php
     - header.php
     - footer.php
     - functions.php
     - page.php
     - 404.php

- populate index.php with the content of the html file

- Separate the header in the header.php and the footer in the footer.php

- Inclue header and footer in the index.php

```php
get_header();
get_footer();
```

- Install classic editor plugin

- Create a new page in the wp dashboard.

- In settings/reading set the homepage to be displayed as a static page and select the page you just created.

- In settings/permalinks choose to be displayed in post name.

- In the header file, delete the links tags, we're gonna enqueue them in the functions.php file. Include in the header the function wp_head(). This functions hooks in functions that we're gonna define in the functions file.

```php
wp_head();
```

- Include in the footer file the following code:

```php
wp_footer();
```

- In functions.php, create a function that is going to load the stylesheets. (repeat the register and the enqueue for each stylesheet)

```php
function myFunction() {
    wp_register_style('<name>', get_template_directory_uri() . '<path to the stylesheet file>', NULL, 1, 'all');

    wp_enqueue_style('<name>');
}
```

- To call the function, add a add_action() outside the function.

```php
add_action('wp_enqueue_scripts', myFunction)
```

- Create a second function to load the js files.

```php
function myFunction(){
    wp_register_script('<name>', get_template_directory_uri().'<path to the js file>', NULL, 1, 'all');

    wp_enqueue_script('<name>')
}
```

- In order to appear, the img tags must point to the main folder:

```php
<img src="<?php echo get_template_directory_uri().'<path to the img>' ?>" alt="">
```

---

## Dynamic with Advanced Custom Fields

- Install the plugin advanced custom fields by Elliot Condon. With that, you have a new tab named "Custom fields". You can create new field to populate your webpage

- Create a new field group (named 'Home page' for example). And add sub-fields for each text you want.

- In location/rules, select "page type" and select the home page. The fields to be filled are gonna be in the home page created before.

- In the code, create a variable to call the group we created in the custom fields plugin.

```php
$hero = get_field('<name of the field>');
```

- Then, echo it (it's an assoc array) in the proper places. The name should be the name of the field. Ex:

```php
<h1> <?php echo $hero['title']  ?> </h1>
```

---

## Dynamic with widgets

- Create a widget for the dashboard. (it will be found in appearence/widgets and we will be able to add text,img,etc. to each widget).
  In functions.php:

```php
add_action('widgets_init', 'myFunction');

function myFunction(){
    register_sidebar(
        array(
            'name' => 'Banner',
            'id' => 'banner',
            'description' => 'Type any text here',
            'before_widget' => '<div class="widget-wrapper">',
            'after_widget' => '</div>',
            'before_title' => '<h2 class="widget-title">',
            'after_title' => '</h2>'
        )
    );
};
```

- Add the placeholder of the widget in index.php:

```php
if(is_active_sidebar('banner')){
    dynamic_sidebar('banner');
}
```

- In the dashboard, fill the widgets with text, img, etc.

## Working with posts

- The loop. Example:

```php
while(have_posts()){
    the_post();
    <h1><?php the_title() ?></h1>
    <p><?php the_content() ?></p>
    <span> <?php the_time() ?> </span>
}
```
