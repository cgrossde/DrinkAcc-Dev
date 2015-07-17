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

### Install problems

Should the initial run of `composer install` throw errors, then try to fix them or just run `composer install again`. Once composer installed all dependencies you can setup Typo3 flow with theses commands:

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
* PhpMyAdmin: http://drinkaccounting.local:1085 | http://localhost:10850

## Accounts

**MySQL:**
Admin: root:secret
Drinkaccounting DB: drinkaccounting (drinkaccounting:secret)

## Logs

```
# Ngix
less /var/log/nginx/drinkacc.dev.log
less /var/log/nginx/drinkacc.prod.log
# Typo3 Flow
less /var/www/html/Data/Logs/System_Development.log
less /var/www/html/Data/Logs/System_Production.log
```

## Useful commands

```
# Flush cache or delete everything in Data/Temporary
./flow flow:cache:flush
# Update database after changes to models
./flow doctrine:update
# Show log
tail -f Data/Logs/System_Development.log
# Or if in production context
tail -f Data/Logs/System_Production.log
```
