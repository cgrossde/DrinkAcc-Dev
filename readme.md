# Drinkaccounting distribution package

See: https://github.com/cgrossde/CGROSS.Drinkaccounting

## Install

Add the line

```
192.168.33.10 drinkacc.dev drinkacc.prod
```

to your `/etc/hosts` or `C:\ Windows\System32\drivers\etc\hosts`.

Open a shell and execute `vagrant up`. Vagrant will now get a VM and install all the necessary software in it.

Vagrant synchronises the `html` folder into the VM at `/var/www/html`, so just use your favorite Text-Editor and edit the files on the host machine in the `html` folder.

## Better performance / Symlink problems

For better performance and to fix symlink problems exec on Windows: `vagrant plugin install vagrant-winnfsd`
On Mac OS or linux exec: `vagrant plugin install vagrant-bindfs`

### Install problems

Should the initial run of `composer install` throw errors, then try to fix them or just run `composer install` again. Once composer installed all dependencies you can setup Typo3 flow with theses commands:

```
# Repeat until all dependencies are present and no more errors occur
composer install

# Setup typo3 flow
./flow core:setfilepermissions vagrant vagrant vagrant
./flow doctrine:migrate
./flow doctrine:update
```

## Services

* Website dev context (less caching): http://drinkacc.dev
* Website production context: http://drinkacc.prod
* PhpMyAdmin: http://drinkacc.dev:1085 | http://localhost:10850

## Accounts

**MySQL:**
Admin: root:secret
Drinkaccounting DB: drinkaccounting (drinkaccounting:secret)

## Logs

```
# Production: drinkacc.prod
multitail /var/log/nginx/drinkacc.prod.log /var/www/html/Data/Logs/System.log
# Development: drinkacc.dev
multitail /var/log/nginx/drinkacc.dev.log /var/www/html/Data/Logs/System_Development.log
```

## Useful commands

```
# Flush cache or delete everything in Data/Temporary
./flow flow:cache:flush
# Update database after changes to models
./flow doctrine:update
# List all commands
./flow help
```

## Useful sites

* http://flow.typo3.org/documentation/quickstart
* http://flow.typo3.org/documentation/guide
* http://flow.typo3.org
* http://google.de
