# devenv.sh environment for Magento 2 development

[devenv](https://devenv.sh) it's a powerful development environment based on [NixOS](https://nixos.org).  
It allows you to have containerized environments without containers or hypervisor or emulation, with native performance on any platform.  
This is by far the fasted Magento/Openmage development environment I've ever worked with and it's more than worth of the time to learn it.

This repo has a basic (and yet complete) [OpenMage](https://github.com/OpenMage/magento-lts) project installed via composer and all of the necessary software stack:
- PHP 8.1 (managed by PHP-FPM and served by [Caddy](https://caddyserver.com))
- MySQL 8.0
- redis 7.0
- Elasticsearch 7
- Xdebug 3.2
- [MailHog](https://github.com/mailhog/MailHog) for email testing
- n98-magerun2

# Install the environment

1. If you don't have devenv/NixOS installed please follow [devenv's installation guide](https://devenv.sh/getting-started), it's actually pretty easy and straightforward.
2. Then clone this repository to have all the configuration files on your machine

# Install Magento 2

1. Start all services with `devenv up`
2. Open another terminal
3. Enter the development environment shell with `devenv shell`
4. Create the magento project in the magento2 folder with composer `create-project --repository-url=https://mirror.mage-os.org/ magento/project-community-edition:2.4.5 magento2`
5. `cd magento2`
6. `composer install`


# Startup the environment

1. Enter the cloned repo's directory
2. run `devenv up`, this will start all the software stack (and also run composer install for you)

At the moment the project is configured with `http://magento2.test` as the main domain name (you can change it in the `devenv.nix` file), so you'll have to add `magento2.test`to your `hosts` file first, then you'll be able to open the browser to `http://magento2.test`.
