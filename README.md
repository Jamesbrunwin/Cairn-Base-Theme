# Base (parent) theme

## Template tags (overridable)

If you'd like to override any of these functions, create a new function in
your functions.php file with the same name. Your function will overwrite 
the original.

### `cairn_get_img_url($file)` 

Return the full url of image `$file` (includes TEMPLATE_DIRECTORY/images/).

### `cairn_img_url($file)`

echos `cairn_get_img_url` 

### `cairn_get_post_thumbnail_src($post_id, $size)`

Return the post thumbnail src for given post id and thumbnail size.

Defaults to current post and 'full'.

### `cairn_post_thumbnail_src($post_id, $size)`

echos `cairn_get_post_thumbnail_id`

### `cairn_register_nav_menus`

Adds nav menus to the site. See also: `cairn_register_nav_menus` action

### `cairn_add_theme_support`

Adds post thumbnail support to the theme. Override to remove post thumbnail 
support, or to add more support (post-formats, etc);

## Actions

Because the base theme does some grafting in the background, there are some
actions which it creates which you can hook onto. If possible, you should
use these instead of the standard WP versions (replace `wp_` with `cairn_`);

### `cairn_init`

Stuff which should run on wp_init

### `cairn_admin_enqueue_styles`

Use to enqueue styles in the admin area

### `cairn_enqueue_styles`

Use to enqueue styles

```
add_action('cairn_enqueue_styles', 'SITENAME_enqueue_styles');

function SITENAME_enqueue_styles() {
  wp_enqueue_style(...);
}

```

### `cairn_enqueue_scripts`

Use to enqueue scripts

```
add_action('cairn_enqueue_scripts', 'SITENAME_enqueue_scripts');

function SITENAME_enqueue_scripts() {
  wp_register_script(...);
  wp_enqueue_script(...);
}

```

### `cairn_register_nav_menus`

Use to add new nav menus. You can use this instead of overriding the 
`cairn_register_nav_menus` function. 

```
add_action('cairn_register_nav_menus', 'SITENAME_register_nav_menus');

function SITENAME_register_nav_menus() {
  register_nav_menus(array(
    // ...
  ));
}
```
