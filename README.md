# Crontab Component

Crontab provide a php 5.3 lib to create crontab file.

```
use Crontab\Crontab;
use Crontab\Job;

$job = new Job();
$job
    ->setMinute('*/5')
    ->setHour('*')
    ->setDayOfMonth('*')
    ->setMonth('1,6')
    ->setDayOfWeek('*')
    ->setCommand('myAmazingCommandToRunPeriodically');

$crontab = new Crontab();
$crontab->addJob($job);
$crontab->write();
```
You can render what you have created:

```
echo $crontab->render();
```

And then you can delete a job you don't want anymore:
```
$crontab->removeJob($theJobYouWantToDelete);
```

When you create a Crontab, it will automatically parse your current crontab file and add all present job into your new object.

Explicitly set the constructor argument `$parseExistingCrontab` to false if you do not want to parse the current crontab file. 

## Resources

You can run the unit tests with the following command. You need to be in the crontab directory and have phpunit installed on your computer:

```
phpunit -v
```


## Acknowledgements

This was taken from the original package by Yzalis and republished as it is used with an internal project. Any changes made will be to fix functionality broken with this project and not to improve the project (as yet).