---
layout: post
title:  Import Data From Excel to MySQL/ MariaDB.
date:   2016-02-26 14:40
modified: 2016-08-07 01:28
categories: data maria mysql excel
tags: [mariadb, phpmyadmin, excel, migration]
excerpt: "How to import data from Excel to MySQL/ MariaDB using LOAD DATA INFILE command."
comments: true
---

Suppose we have a table called `invitees` in `event_2016` database. The `invitees` table structure is as follows.

{% highlight MySQL %}
> USE event_2016;
> DESC invitees;
+----------------+------------------+------+-----+---------------------+----------------+
| Field          | Type             | Null | Key | Default             | Extra          |
+----------------+------------------+------+-----+---------------------+----------------+
| id             | int(10) unsigned | NO   | PRI | NULL                | auto_increment |
| name           | varchar(64)      | NO   |     | NULL                |                |
| email          | varchar(64)      | NO   | UNI | NULL                |                |
| job_title      | varchar(64)      | YES  |     | NULL                |                |
| company        | varchar(64)      | YES  |     | NULL                |                |
| has_registered | tinyint(1)       | YES  |     | 0                   |                |
+----------------+------------------+------+-----+---------------------+----------------+
{% endhighlight %}

## Processing Data in Excel

First thing first, we need to convert invitees data in Excel file ( \*.xlsx, \*.xls, OR \*.ods) to text file (\*.csv OR \*.tsv). In this example, data converted to \*.csv file. So that it looks like this:

{% highlight bash %}
name, email, job_title, company
Abu Bakr as-Shiddiq,abu@calipha.te,1st caliph,The Caliphate Inc.
Umar ibn Al-Khattab,umar@calipha.te,2nd caliph,The Caliphate Inc.
Uthman ibn Affan,uthman@calipha.te,3rd caliph,The Caliphate Inc.
Ali ibn Abi-Talib,ali@calipha.te,4th caliph,The Caliphate Inc.
{% endhighlight %}

## Import Data to MySQL/ MariaDB

* Import the \*.csv data to `invitees` table using `LOAD DATA INFILE` command:

{% highlight MySQL %}
> LOAD DATA INFILE '/home/user/invitee.csv'
    -> INTO TABLE invitees
    -> FIELDS TERMINATED BY ','
    -> LINES TERMINATED BY '\n'
    -> IGNORE 1 LINES
    -> (name, email, job_title, company);

Query OK, 4 rows affected (0.05 sec)
Records: 4  Deleted: 0  Skipped: 0  Warnings: 0
{% endhighlight %}

* Check your imported data in the table:

{% highlight MySQL %}
> SELECT * FROM invitees;
+----+---------------------+--------------------+-------------+----------------+----------------+
| id | name                | email              | job\_title   | company        | has\_registered |
+----+---------------------+--------------------+-------------+----------------+----------------+
|  1 | Abu Bakr as-Shiddiq |  abu@calipha.te    |  1st caliph |  The Caliphate |              0 |
|  2 | Umar ibn Al-Khattab |  umar@calipha.te   |  2nd caliph |  The Caliphate |              0 |
|  3 | Uthman ibn Affan    |  uthman@calipha.te |  3rd caliph |  The Caliphate |              0 |
|  4 | Ali ibn Abi-Talib   |  ali@calipha.te    |  4th caliph |  The Caliphate |              0 |
+----+---------------------+--------------------+-------------+----------------+----------------+
{% endhighlight %}

This practice will save your day if you have thousand or even million rows of data.

Reference:
[LOAD DATA INFILE in MariaDB](https://mariadb.com/kb/en/mariadb/load-data-infile/)
{: .notice}