# HibernateHbm2ddlProperties.CreateDrop

Hbm2ddl properties:
Create – create the schema, the data previously present (if there) in the schema is lost

Update – update the schema with the given values

Validate – validate the schema. It makes no change in DB.

Create-drop – create the schema with destroying the data previously present (if there). It also drops the database schema when the 

SessionFactory is closed.

Important points:
In case of update, if schema is not present in the DB then the schema is created.

In case of validate, if schema does not exist in DB, it is not created. Instead, it will throw an error: - Table not found: <table name>

In case of create-drop, schema is not dropped on closing the session. It drops only on closing the SessionFactory.

Key points:

You can set hibernate.hbm2ddl.auto=update to update your database with changes to your model, but I would not trust that on a product 
database.

Therefore, for our production database, do not set hibernate.hbm2ddl.auto – the default is to make no database changes. Instead, we 

manually create an SQL DDL update script that applies changes from one version to the next.

You may use liquibase or flyway for upgrading your db. hibernate’s schema update feature is really ony good for a developer while they are 

developing new features. In a production situation, the db upgrade needs to be handled mode carefully. 

