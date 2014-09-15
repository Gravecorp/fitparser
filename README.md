fitparser
=========

Drupal eve fit parser

queries to build the itemid.xml file

SQLite:
select '<row typeID="' || typeID || '" typeName="' || replace(replace(replace(typeName, '&', '&amp;'), '''', '&apos;'), '"', '&quot;') || '" />' from invTypes where marketGroupID NOTNULL order by marketGroupID ASC
 
MySQL:
select CONCAT('<row typeID="' ,typeID, '" typeName="', REPLACE(REPLACE(REPLACE(typeName, '&', '&amp;'), '''', '&apos;'), '"', '&quot;'), '" />') from invTypes where marketGroupID IS NOT NULL order by marketGroupID AS

View this file as raw to see the complete queries.

To update the xml db in drupal replace the <row> tags with the new data and bump the version up by 1. zip the folder and deploy the module.
It will auto update the drupal static cache on first call of the module.