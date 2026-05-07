# NoDirectImplementation attribute
This is a stub repository for what will hopefully soon be a PHP extension that allows the langauge to parse a new attribute 
that is applied to interfaces, specifying that they must be extended by other interfaces rather than being implemented 
directly. If a class tries to implement such an interface, a new type of exception should be thrown. 

I will vibe code a proof-of-concept extension when time allows, with the hope that this will eventually be adopted as a feature of the language after a thorough audit by the community. 

Fallback rules for Psalm and PHPStan (and a composer-based installer for them!) should also be provided in a separate repository so that this can be widely adopted. 

An example of how this would be used: 

```

<?php

declare(strict_types=1);

namespace My\Namespace\Interface;

#[NoDirectImplementation(allowedExtenders: 'My\Other\Namespace\HasWeeklyCalendarInterface,My\Other\Namespace\HasMonthlyCalendarInterface')]
interface HasCalendarInterface
{
  public function getCalendar(): string;
}

```

### Instructions for installation of extension

todo. Assume we have docker 

### A few things to keep in mind: 

* The allowedExtenders list can contain a mix of interfaces in the same namespace and interfaces in other
  namespaces. Only the latter require fully qualified class names.
* The allowedExtenders list is optional. If not provided, all other interfaces are allowed to extend.
* The extension should live in this repository. The static analysis rules and composer installer for them
  should live in its own repository to avoid things becoming confusing for people who want to try the system
  out.
* An extensive test rig for this extension should live in a third repository to keep this one clean. 
* etc.,.
