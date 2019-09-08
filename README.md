# Need and use of Liquibase?
We are using version control tool for our Java and other languages to manage, track and apply changes whenever required.
Liquibase is an open source tool for database version control.
Using Liquibase we can manage, tack and apply changes using simple human readable changelog files.

# Spring Boot 2 Liquibase Integration
In this sample application H2(In Memory Database) is used to show simple integration of Liquibase using change log files.

We can use different small change log files to manage our DB changes .
In this example we have one master changeloge file (changelog-master.xml)
```
<?xml version="1.0" encoding="UTF-8"?>
<databaseChangeLog
        xmlns="http://www.liquibase.org/xml/ns/dbchangelog"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xmlns:ext="http://www.liquibase.org/xml/ns/dbchangelog-ext"
        xsi:schemaLocation="http://www.liquibase.org/xml/ns/dbchangelog http://www.liquibase.org/xml/ns/dbchangelog/dbchangelog-3.1.xsd
    http://www.liquibase.org/xml/ns/dbchangelog-ext http://www.liquibase.org/xml/ns/dbchangelog/dbchangelog-ext.xsd">

    <include file="/db/changelog/changes/create-application-information-table-changelog.xml"/>
    <include file="/db/changelog/changes/insert-application-information-table-changelog.xml"/>
    <include file="/db/changelog/changes/update-application-information-table-changelog.xml"/>
</databaseChangeLog>
```
And we have different sub change log files -
  create-application-information-table-changelog.xml
  insert-application-information-table-changelog.xml
  update-application-information-table-changelog.xml
  
All above sub change log files are imported in master file - 
```
<include file="/db/changelog/changes/create-application-information-table-changelog.xml"/>
<include file="/db/changelog/changes/insert-application-information-table-changelog.xml"/>
<include file="/db/changelog/changes/update-application-information-table-changelog.xml"/>
```
Above sub change file will create table in database, insert data in table and update records of the table when you run the application.
You can specify order of the excution of each changes in change log file.

Read More - https://www.liquibase.org/
