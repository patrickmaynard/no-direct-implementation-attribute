# no-direct-implementation-attribute
This is a stube repository for what will hopefully soon be a PHP extension that allows the langauge to parse a new attribute that is applied to interfaces, specifying that they must be extended by other interfaces rather than being implemented directly. 

I will vibe code a proof-of-concept extension when time allows, with the hope that this will eventually be adopted as a feature of the language. 

Fallback rules for Psalm and PHPStan should also be provided so that this can be widely adopted. 

An example of how this would be used: 

```

<?php

declare(strict_types=1);

namespace App\Service\Interface;

//The allowedExtenders list is optional.
//If not provided, all other interfaces are allowed to extend.

#[NoDirectImplementation(allowedExtenders: 'My\Namespace\HasWeeklyCalendarInterface,My\Namespace\HasMonthlyCalendarInterface')]
interface HasCalendarInterface
{
  public function getCalendar(): string;
}

```
