# Custom DQL Time functions
Get custom time function in Doctrine Query Langage (DQL)

## Contains
- Time_diff : difference between two DateTime PHP object
- Time_add  : add an amount of time to a DateTime
- Time_sub  : sub an amount of time to a DateTime

## Installation
- Symfony/app/config/config.yml :
```
(...)
doctrine:
    (...)
    orm:
        (...)
        dql:
            numeric_functions:
                time_diff: DQL\TimeDiff
                time_add: DQL\TimeAdd
                time_sub: DQL\TimeSub
```

- Copy src/DQL/TimeAdd.php src/DQL/TimeDiff.php src/DQL/TimeSub.php to your Symfony/src/DQL/

## Usages
In your DQL request
```
TIME_DIFF(DateTime1, DateTime2, unit)
TIME_ADD(DateTime, interval, unit)
TIME_SUB(DateTime, interval, unit)
```

## Examples
```
$em->createQuery("... TIME_ADD(:date, 12, 'minute') ...")
   ->setParameters(array('date' => $dateTime));
```

```
$em->createQuery("... TIME_SUB(:date, 24, 'hour') ...")
   ->setParameters(array('date' => $dateTime));
```
Equivalent to :
```
$em->createQuery("... TIME_SUB(:date, 1, 'day') ...")
   ->setParameters(array('date' => $dateTime));
```

```
$em->createQuery("... TIME_DIFF(:date1, :date2, 'minute') ...")
   ->setParameters(array(
		'date1' => $dateTime1,
		'date2' => $dateTime2
	)); 
```
returns an integer

## Authors
CLARAS Damien & [PLATTEAU Jonathan](http://jonathan.pl/)
