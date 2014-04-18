---
title: Super Custom Login Page
author: Matthew Smith
layout: page
comments:
  - comments
---
This WordPress plugin is based of of BM Custom Login and allows you to change the appearance of the login page (as did the original plugin), in addition to customizing the link and the link title.
This is currently a proof of concept that was hacked together in about an hour. It works, but there is no protection against malicious use built into the plugin (other than what is provided by WordPress). The main concern is that the plugin will accept any string for the URL or URL title without sanitizing it first. This could cause serious issues if not used properly!
Use at your own risk!
I will be updating this shortly with further features and improving the security, so for now there is no download available.
If you want to see it in action, you can see it at the development site.
If you have some suggestions on how to improve it (at the moment, I&#8217;m very interested in the security aspect), please leave a comment!

{% highlight php %}
/*
Plugin Name: Super Custom Login Page
Plugin URI: http://digivation.net/wordpress/super-custom-login-page/
Description: Based on BM Custom Login, you can display custom images on the wordpress login screen and modify the header link. Customize away!
Author: Matthew Smith
Version: 0.01b
Author URI: http://digivation.net/
*/ 
/*
	Functions
*/
// the original BM function, renamed
function sc_login_stylesheet() {
	echo &#8216;
&#8216;;
}
// all new stuff from here down  
// change login link
function sc_login_link($args=null) {
	$sc_customlink = get_option(&#8216;sc_login_url&#8217;);	// get url
	return $sc_customlink;	// return the url
}
// change login link title
function sc_login_linktitle($args=null) {
	$sc_custom_linktitle = get_option(&#8216;sc_login_urltitle&#8217;);	// get the title
	return $sc_custom_linktitle; // return linktitle
}
// uninstall function
function sc_login_remove() {
	// remove title &#038; url options
	delete_option(&#8216;sc_login_url&#8217;);
	delete_option(&#8216;sc_login_urltitle&#8217;);
}
// setup function
function sc_login_setup() {
	// add options (set to default WP values)
	add_option(&#8216;sc_login_url&#8217;,'http://wordpress.org/&#8217;,'The custom URL&#8217;);
	add_option(&#8216;sc_login_urltitle&#8217;,'Powered by WordPress&#8217;,'The custom URL title&#8217;);
}
/*
	Admin Area Stuff
*/
// the admin menu
function sc_admin_menu() {
	// lets print some HTML!
	if( current_user_can(&#8216;manage_options&#8217;) ) {
	?>

Custom Login Page Options
 
			if( $_REQUEST['submit'] ) {
				sc_update_options(); // update options and...
			}
			sc_print_admincontent(); // print other stuff
			sc_print_form(); // print our form
	?>	
 
		} else {
			wp_die(__('You do not have permission to access this page.'));
		}
}
// print messages
function sc_print_admincontent() {
}
function sc_print_form() {
	// get current options
	$sc_current_url = get_option('sc_login_url');
	$sc_current_title = get_option('sc_login_urltitle');
	?>



Custom URL:
&#8221; size=&#8221;40&#8243; />
	Enter the URL you would like the logo to point to (defaults to http://wordpress.org).
	


Custom URL Title:
&#8221; size=&#8221;40&#8243; />
	
	Enter a title for the URL (defaults to &#8220;Powered by WordPress&#8221;).





}
function sc_update_options() {
	$done = false;
	// quick &#038; dirty security check
	if( current_user_can('manage_options') ) {
		// validate input TODO
		// do the updating!
		if( $_REQUEST['custom_url'] ) {
			update_option( 'sc_login_url',url_shorten( $_REQUEST['custom_url'] ) );
			$done = true;
		}
		if( $_REQUEST['custom_title'] ) {
			update_option( 'sc_login_urltitle',$_REQUEST['custom_title'] );
			$done = true;
		}
	} else {
		wp_die(__('You do not have permission to access this page.'));
	} // can current user manage options?
	if( $done ) { ?>

Options saved.


	} else {?>

Error updating options!


	}
}
// create admin menu, under "Presentation"
function sc_admin_menu_setup() {
	add_theme_page(
						'Login Page Options',	// page title, doesn't do anything
						'Customize Login Page',	// menu title
						'manage_options',	// permissions
						__FILE__,	// file
						'sc_admin_menu'	// the function
					);
}
/*
	Hooks
*/
add_action('login_head','sc_login_stylesheet');
add_action('admin_menu','sc_admin_menu_setup');
add_filter('login_headerurl','sc_login_link');
add_filter('login_headertitle','sc_login_linktitle');
register_activation_hook(__FILE__,'sc_login_setup');
register_deactivation_hook(__FILE__,'sc_login_remove');
?>
{% endhighlight %}
