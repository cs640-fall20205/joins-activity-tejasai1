# Using Redis in this course

## Start the database

```
$ ./up.bash
$
```

## Connect to the database

```
$ ./shell.bash
redis>
```

## Disconnect from the database

```
redis> quit
```

## Save your data

```
redis> SAVE
redis> quit
$ cp /tmp/redis-data/dump.rdb dump.rdb
```

## Stop the database

```
$ ./down.bash
```

## Restore your data

```
$ ./up.bash
$ ./down.bash
$ sudo cp dump.rdb /tmp/redis-data/dump.rdb
```

## Start clean after saving (in same GitPod session)

```
$ ./down.bash
$ sudo rm /tmp/redis-data/dump.rdb
$ ./up.bash
```

## Daily workflow

```
## Open your project in GitPod.

## Reposition terminal
$ cd redis

## Restore saved database from last time. (Skip if this is your first time.)
$ ./up.bash
$ ./down.bash
$ sudo cp dump.rdb /tmp/redis-data/dump.rdb

## Start and connect to database
$ ./up.bash
$ ./shell.bash

## Do work
redis>

## Save, disconnect from, and stop database
redis> SAVE
redis> quit
$ cp /tmp/redis-data/dump.rdb dump.rdb
$ ./down.bash

## Save work to GitLab and stop GitPod
$ save-and-stop
```
