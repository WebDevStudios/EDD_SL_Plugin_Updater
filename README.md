# EDD_SL_Plugin_Updater

Find updated copies at https://github.com/awesomemotive/easy-digital-downloads/blob/main/includes/EDD_SL_Plugin_Updater.php

# Example usage

Updater invoking

```
/**
 * Fire up our updater processes.
 *
 * @since 1.0.0
 */
public function updater() {
	$config          = [
		'license_key' => get_option( PREMIUM_PLUGIN_SLUG . '_license_key', '' ),
		'store_url'   => PREMIUM_STORE_URL,
		'version'     => PREMIUM_VERSION,
		'item_name'   => PREMIUM_PLUGIN_NAME,
	];
	$license_handler = new Updater( $config );
	$license_handler->do_update();
}
```

```
<?php
/**
 * Updater Class file
 *
 * @package WebDevStudios\namespace
 * @since   1.0.0
 */

namespace WebDevStudios\namespace;

require_once PREMIUM_PATH . 'vendor/autoload.php';

/**
 * Class Updater
 *
 * @since 1.0.0
 */
class Updater {

	/**
	 * Domain to check for updates at.
	 *
	 * @var string
	 */
	private $store_url;

	/**
	 * License key to check.
	 *
	 * @var string
	 */
	private $license_key;

	/**
	 * Current installed version.
	 *
	 * @var string
	 */
	private $version;

	/**
	 * Product name to check.
	 *
	 * @var string
	 */
	private $item_name;

	/**
	 * Constructor
	 *
	 * @param array $config Array of Updater configuration settings.
	 *
	 * @since 1.0.0
	 */
	public function __construct( array $config = [] ) {
		$this->store_url   = $config['store_url'];
		$this->license_key = $config['license_key'];
		$this->version     = $config['version'];
		$this->item_name   = $config['item_name'];
	}

	/**
	 * Run our updater process.
	 *
	 * @since 1.0.0
	 */
	public function do_update() {
		$edd_updater = new \EDD_SL_Plugin_Updater(
			$this->store_url,
			MAIN_PREMIUM_FILE,
			[
				'version'   => $this->version,
				'license'   => $this->license_key,
				'item_name' => $this->item_name,
				'author'    => 'Pluginize',
			]
		);
	}
}
```
