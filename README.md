# no-direct-implementation-attribute
This will be a PHP extension that allows the langauge to parse a new attribute that is applied to interfaces, specifying that they must be extended by other interfaces rather than being implemented directly. 

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
