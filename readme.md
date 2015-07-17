# Drinkaccounting distribution package

See: https://github.com/cgrossde/CGROSS.Drinkaccounting

## Install

Add the line

```
192.168.33.10 drinkaccounting.local
```

to your `/etc/hosts` or `C:\ Windows\System32\drivers\etc\hosts`.

Open a shell and execute `vagrant up`. Vagrant will now get a VM and install all the necessary software in it.

Vagrant synchronises the `html` folder into the VM at `/var/www/html`, so just use your favorite Text-Editor and edit the files on the host machine in the `html` folder.

## Services

* Website: http://drinkaccounting.local | http://localhost:8000
* PhpMyAdmin: http://drinkaccounting.local:1085 | http://localhost:10850
* Mailcatcher: http://drinkaccounting.local:1080 | http://localhost:10800

## Accounts

**MySQL:**
Admin: root:secret
Drinkaccounting DB: drinkaccounting (drinkaccounting:secret)
