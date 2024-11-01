=== Plugin Name ===
Contributors:        christopher.amirian
Plugin Name:         UIKIT WP Integrator
Plugin URI:          https://github.com/iconoclastic/uikit-wordpress-integrator
Tags:                uikit, yootheme, integrate, embed, front-end, framework, Wordpress
Author URI:        	 https://github.com/iconoclastic
Author:              Christopher Amirian
Donate Link:         https://github.com/iconoclastic
Requires at least:   3.9
Tested up to:        3.9.1
Stable tag:          1.1.1
Version:             1.1.1
License:             GPLv2 or later
License URI:         http://www.gnu.org/licenses/gpl-2.0.html

Wordpress plugin for integrating UIKIT front-end framework from yootheme.com 

== Description ==

<h3>General Information</h3>

**UIKIT WP Integrator** is a plugin for integrating [UIKIT](http://getuikit.com/ "UIKIT") front-end framework from [YOOTHEME](http://yootheme.com/ "Yootheme").

The plugin adds a menu item under *Settings* in Dashbpard called **UIKIT Integrator** which enables you to configure how you want the UIKIT framework integrated into your website front-end.  

**`UIKIT WP Intergrator` currently is using `UIKIT` version `2.8.0`**

<h3>Here is the list of settings available:</h3>

* **Please select the style of UIKIT you want to integrate**

    1. Gradient
    2. Almost Flat
    3. Flat 

    *UIKIT can be added in 3 styles:*  
    
     * Gradient: Using CSS3 gradients and new state of the art codes to keep with modern standards     
     * Almost Flat: Using mixture of flat and CSS3 stuff  
     * Flat: No use of new CSS3 features, good for websites that want to support old browsers  
    

* **Please select the desired addon you want to enable**

    1. Autocomplete
    2. Datepicker
    3. Form Password
    4. Form Select
    5. HTML Editor
    6. Nestable
    7. Notify
    8. Pagination
    9. Search
    10. Sortable
    11. Sticky
    12. Timepicker
    13. Upload

    *For more information about Addons please visit: [UIKIT ADDONS](http://www.getuikit.com/docs/addons.html "UIKIT ADDONS")*

    **Please use links below for more information about each addon:**

    * [Autocomplete](http://www.getuikit.com/docs/addons_autocomplete.html "Autocomplete")   
    * [Datepicker](http://www.getuikit.com/docs/addons_datepicker.html "Datepicker")
    * [Form Password](http://www.getuikit.com/docs/addons_form-password.html "Form Password")
    * [Form Select](http://www.getuikit.com/docs/addons_form-select.html "Form Select")
    * [HTML Editor](http://www.getuikit.com/docs/addons_htmleditor.html "HTML Editor")
    * [Nestable](http://www.getuikit.com/docs/addons_nestable.html "Nestable")
    * [Notify](http://www.getuikit.com/docs/addons_notify.html "Notify")
    * [Pagination](http://www.getuikit.com/docs/addons_pagination.html "Pagination")
    * [Search](http://www.getuikit.com/docs/addons_search.html "Search")
    * [Sortable](http://www.getuikit.com/docs/addons_sortable.html "Sortable")
    * [Sticky](http://www.getuikit.com/docs/addons_sticky.html "Sticky")
    * [Timepicker](http://www.getuikit.com/docs/addons_timepicker.html "Timepicker")
    * [Upload](http://www.getuikit.com/docs/addons_upload.html "Upload")

    *Please be advised that if you are already using WARP enabled Yootheme, theme you don't need this plugin as UIKIT is already integrated for you*

== Installation ==

To install UIKIT WP Integrator plugin follow this steps:

1. Download plugin zip file 
2. Upload `uikit-wordpress-integrator` directory into to the `/wp-content/plugins/` directory
3. Activate the plugin through the 'Plugins' menu in WordPress

*Visit UIKIT Integrator menu item under Settings inside Dashboard to configure the plugin*

== Frequently Asked Questions ==

= Do I need this plugin if I purchased a theme from Yootheme? =

No, your theme already has the UIKIT framework integrated

= Can I use UIKIT without addons? =

Yes, just uncheck addons from settings page of the plugin located under Settings -> UIKIT Integrator menu

= How can I enable UIKIT menu inside my theme =

Add this code inside `functions.php` of your theme:

	add_theme_support( 'menus' );
	if (function_exists('register_nav_menus')) {
		$locations = array(
			'primary' => 'Primary Navigation'
		);
		register_nav_menus( $locations );
	}

	function nav_menu_item_parent_classing( $classes, $item )
	{
	    global $wpdb;
	    
	$has_children = $wpdb -> get_var( "SELECT COUNT(meta_id) FROM {$wpdb->prefix}postmeta WHERE meta_key='_menu_item_menu_item_parent' AND meta_value='" . $item->ID . "'" );
	    
	    if ( $has_children > 0 )
	    {
	        array_push( $classes, "uk-parent" );
	    }
	    
	    return $classes;
	}

	add_filter( "nav_menu_css_class", "nav_menu_item_parent_classing", 10, 2 );

	class Child_Wrap extends Walker_Nav_Menu
	{
	    function start_lvl(&$output, $depth = 0, $args = array())
	    {
	        $indent = str_repeat("\t", $depth);
	        $output .= "\n$indent<div class=\"uk-dropdown uk-dropdown-navbar\"><ul class=\"uk-nav uk-nav-navbar\">\n";
	    }
	    function end_lvl(&$output, $depth = 0, $args = array())
	    {
	        $indent = str_repeat("\t", $depth);
	        $output .= "$indent</ul></div>\n";
	    }
	}	

== Changelog ==

= 1.1.1 =

* Integrates UIKIT Version 2.8.0

= 1.1.0 =

* Integrates UIKIT Version 2.7.0
* **WARNING:** UIKIT version 2.7.0 has some code changes that may break if you want to update from 2.6.0. Please visit [THIS LINK](http://www.yootheme.com/blog/2014/06/10/uikit-27-released "UIKIT 2.7.0 Release Notes") for more information 

== Upgrade Notice ==

There is no update notice available yet.

== Screenshots ==

1. Here's a screenshot of settings page