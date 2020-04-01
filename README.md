# vvv-aliases
Host-machine aliases to simplify VVV interactions.

## Installation

1. Add `export VVV_INSTANCE_DIR="[VVV_PATH]"` to your `.bashrc` or `.zshrc`, replacing `[VVV_PATH]` with the full path where VVV's Vagrantfile is found. For example, if your username is `bob` and you checked it out to `~/vvv`, then `[VVV_PATH]` would be replaced with `/Users/bob/vvv`.
1. Add this repository's `bin` directory to your `$PATH`. For example, if you checked this repo out to `~/vvv-aliases`, then you would add `$HOME/vvv-aliases/bin` to your `$PATH`.
1. Open a new terminal window and run the command `which xdebug`. A path should be returned; if `xdebug not found` is shown, verify the path added in the preceding step.

## Commands

### `xdebug`

Toggle the Xdebug module on and off. Xdebug significantly slows down PHP requests, and should only be enabled when actively used.

Usage:

```bash
xdebug on

xdebug off
```

### `wp`

Run WP-CLI commands within Vagrant, returning the result before exiting the VM.

Usage:

```bash
user@MacBook:~/vvv/www/wordpress/public_html/wp-content$ wp option get home
cd /srv/www/wordpress/public_html/wp-content; wp option get home

https://www.wordpress.test

Connection to 127.0.0.1 closed.
user@MacBook:~/vvv/www/wordpress/public_html/wp-content$
```

Note that if a command requires access to a file, the file must exist within the VM and the command must reference the file using its path within the VM.

Additionally, commands that use quoted arguments cannot be run through this passthrough script. In those situations, use `vcd`.

### `vcd`

Switch to the current directory within the VM.

Usage:

```bash
user@MacBook:~/vvv/www/wordpress/public_html/wp-content$ vcd

vagrant@vvv:/srv/www/wordpress/public_html/wp-content$ wp option set test --format=json '{"1":true,"2":false}'

```
