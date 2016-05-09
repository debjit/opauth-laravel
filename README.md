####This branch is only for reference and is not longer supported.
#### If you're using Laravel 4, checkout the branch for Laravel 4.
#### If you're using Laravel 5, checkout the branch for Laravel 5.
# Opauth For Laravel 3.x
__Version 0.2 - Release Date: 17.01.2013__

**This is based on Opauth - http://opauth.org/**

Authorize users with your application implementing multiple Oauth2 providers.

## Currently Supported

- Facebook
- Twitter

**I've only tested it with Facebook. This does not mean that it won't work for other Oauth2 providers. Refer to http://opauth.org/ for help on implementing it.**

## Usage Example

http://example.com/opauth-bundle/public/facebook

```
Route::get('/', array('uses' => 'home@index'));

Route::get('facebook, facebook/(:any)', array('as' => 'facebook', function() {
	Laravel\IoC::resolve('opauth-facebook');
}));

Route::post('done', array('as' => 'done', function(){
	$response = unserialize(base64_decode( $_POST['opauth'] ));
    echo '<pre>';
    print_r($response);
    echo '</pre>';
}));
```

After authorizing you'll be redirect to a link you've specified in:
/bundles/opauth/start.php

```
$config = array(
	'Strategy' => array(
		'Facebook' => array(
			'app_id' => 'YOUR_APP_ID',
			'app_secret' => 'YOUR_APP_SECRET'
		)		
	),
	'security_salt'	=> 'YOURSALTGOESHERE!',
	'path' 			=> '/opauth-bundle/public/',
	'callback_transport' => 'post',
	'callback_url'	=> '/opauth-bundle/public/done'
);
```
 
##DO NOT FORGET TO CHANGE YOUR APP_ID & APP_SECRET