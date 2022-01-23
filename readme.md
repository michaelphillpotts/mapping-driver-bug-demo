#Steps to create:
```
symfony new --version=lts mapping-driver-bug-demo

symfony composer require orm
symfony composer require symfony/maker-bundle --dev
echo 8 > ./.php-version
``` 

Add `type: attribute` to doctrine.orm.mappings.App

Create a separate `temp-vendors` structure to emulate a Bundle in vendors using annotations

Add PSR mapping for `ABCBundle` in `composer.json`

>symfony composer dump-auto

Add `ABCBundle` to `bundles.php`

#To replicate:

>symfony console make:entity FailedEntity
 
Expect: Entity to be created without error and with attributes

Actual
* Entity created with error 'Only annotation or attribute mapping is supported by make:entity'
* Entity created with _annotations_

#To confirm normal behavior:

Comment out `ABCBundle` in `bundles.php`

New entities are now created without error and with attributes 