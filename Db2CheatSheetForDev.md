## Db2 Cheat Sheet for development

* Created by: Andres Gomez Casanova [@angoca](http://twitter.com/angoca)
* Version: 2021-02-23

Get the most recent version at [https://angoca.github.com/db2-cheat-sheet](https://angoca.github.com/db2-cheat-sheet)

* Execution of a file in the console (db2clp).
  * Semi-colon separated sentences:
    * [db2 -t](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.cmd.doc/doc/r0010410.html)
  * At sign separated sentences (when there is SQL PL code):
    * [db2 -td@](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.cmd.doc/doc/r0010410.html)
* Define a terminator character:
  * [--#SET TERMINATOR @](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.apdv.sqlpl.doc/doc/t0009220.html)
* List all databases (aliases):
  * [LIST DB DIRECTORY](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.cmd.doc/doc/r0001961.html)
* Connect to a database (alias):
  * [CONNECT TO mydb](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000906.html)
* Disconnect from a database:
  * [CONNECT RESET](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000906.html)
  * [TERMINATE](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.cmd.doc/doc/r0001973.html)
* Get values from the environment (registry values).
  * Current timestamp:
    * [VALUES CURRENT TIMESTAMP](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0001024.html)
  * Connected user:
    * [VALUES CURRENT USER](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0005886.html)
  * Current database:
    * [VALUES CURRENT SERVER](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0005882.html)
* List all tables:
  * [LIST TABLES](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.cmd.doc/doc/r0001967.html)
  * [LIST TABLES FOR SCHEMA myuser](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.cmd.doc/doc/r0001967.html)
  * [LIST TABLES FOR ALL](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.cmd.doc/doc/r0001967.html)
* Change current schema:
  * [SET CURRENT SCHEMA otherschema](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0001016.html)
* Change the isolation level 
(RR, RS, CS, UR):
  * [SET ISOLATION RR](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0010944.html)
* List all tablespaces with their status:
  * [LIST TABLESPACES](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.cmd.doc/doc/r0002004.html)
* Describe the structure of the table:
  * [DESCRIBE TABLE tbl1](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.cmd.doc/doc/r0002019.html)
* Describe the result of a query:
  * [DESCRIBE SELECT * FROM tbl1](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.cmd.doc/doc/r0002019.html)
* Get help for a Db2 command:
  * [? command](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.cmd.doc/doc/t0011306.html)
* Get help for a SQL code (SQLXXXX) or SQLstate (YYYYY):
  * [? SQLXXXX](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.cmd.doc/doc/t0011305.html)
  * [? YYYYY](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.cmd.doc/doc/t0011305.html)

# DDL

* Create a schema:
  * [CREATE SCHEMA sch1](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000925.html)
* Create a table specifying primary key:
  * [CREATE TABLE tbl1 (col1 CHAR(1) NOT NULL PRIMARY KEY)](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000927.html)
  * [CREATE TABLE tbl2 (col1 INT NOT NULL, col2 DATE NOT NULL, PRIMARY KEY (col1, col2))](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000927.html)
* Create a table specifying tablespaces:
  * [CREATE TABLE tbl3 (col1 INT NOT NULL, col2 CHAR(1)) IN ts1 INDEX IN ts2](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000927.html)
* Create a table specifying schema:
  * [CREATE TABLE sch1.tbl4 (col1 INT)](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000927.html)
* Create a table with auto incremental column:
  * [CREATE TABLE tbl5 (col1 INT NOT NULL GENERATED AS IDENTITY)](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000927.html)
* Create a table like another one:
  * [CREATE TABLE tbl6 LIKE tbl1 IN ts1 INDEX IN ts2](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000927.html)
* Comment on table and column:
  * [COMMENT ON TABLE tbl1 IS 'Comment in table'](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000901.html)
  * [COMMENT ON COLUMN tbl1.col1 IS 'Description of the field'](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000901.html)
* Declare a temporary table (session schema):
  * [DECLARE GLOBAL TEMPORARY TABLE tmp1 (col1 INT, col2 DATE) ON COMMIT PRESERVE ROWS](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0003272.html)
* Create a global temporary tablespace:
  * [CREATE GLOBAL TEMPORARY TABLE tmp2 (col1 INT)](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0053719.html)
* Create an index:
  * [CREATE INDEX idx1 ON tbl2 (col2)](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000919.html)
* Create a unique index:
  * [CREATE UNIQUE INDEX idx2 ON tbl5 (col)](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000919.html)
* Drop an index:
  * [DROP INDEX idx1](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000945.html)
* Add a column (requires Reorg table):
  * [ALTER TABLE tbl1 ADD COLUMN col3 timestamp](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000888.html)
* Change nullability:
  * [ALTER TABLE tbl1 ALTER COLUMN col3 SET NOT NULL](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000888.html)
* Drop nullability:
  * [ALTER TABLE tbl1 ALTER COLUMN col3 DROP NOT NULL](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000888.html)
* Rename a column:
  * [ALTER TABLE tbl1 RENAME COLUMN col3 TO new3](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000888.html)
* Drop column:
  * [ALTER TABLE tbl1 DROP COLUMN new3](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000888.html)
* Create a primary key constraint:
  * [ALTER TABLE tbl5 ADD CONSTRAINT pkt5 PRIMARY KEY (col1)](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000888.html)
* Drop primary key:
  * [ALTER TABLE tbl5 DROP PRIMARY KEY](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000888.html)
* Add identity:
  * [ALTER TABLE tbl2 ALTER col1 SET GENERATED ALWAYS AS IDENTITY](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000888.html)
* Restart identity:
  * [ALTER TABLE tbl2 ALTER col1 RESTART WITH 1](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000888.html)
* Drop identity:
  * [ALTER TABLE tbl2 ALTER col1 DROP IDENTITY](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000888.html)
* Create a foreign key:
  * [ALTER TABLE tbl5 ADD CONSTRAINT fkt5 FOREIGN KEY (col1) REFERENCES tbl11 (col1)](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000888.html)
* Create a check constraint:
  * [ALTER TABLE tbl1 ADD CONSTRAINT chk CHECK (col1 in ('a', 'b', 'c'))](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000888.html)
* Enforce a constraint:
  * [ALTER TABLE tbl1 ALTER CHECK chk ENFORCED](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000888.html)
* Not enforce a constraint:
  * [ALTER TABLE tbl5 ALTER FOREIGN KEY fkt5 NOT ENFORCED](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000888.html)
* Change the granularity of the locks:
  * [ALTER TABLE tbl1 LOCKSIZE TABLE](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000888.html)
* Drop a table:
  * [DROP TABLE tbl1](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000945.html)
* Rename a table:
  * [RENAME TABLE tbl2 TO table2](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000980.html)
* Truncate a table:
  * [TRUNCATE TABLE tbl1 IMMEDIATE](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0053474.html)
* Create a sequence:
  * [CREATE SEQUENCE seq AS INTEGER](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0004201.html)
* Restart sequence:
  * [ALTER SEQUENCE seq RESTART WITH 15](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0004200.html)
* Create a stored procedure:
  * [CREATE OR REPLACE PROCEDURE prc1 (IN val INT, OUT ret DATE) SPECIFIC mypr BEGIN SET ret = (SELECT col2 FROM tbl2 WHERE col1 = val); END @](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0008329.html)
* Create a trigger:
  * [CREATE TRIGGER cp_val AFTER INSERT ON tbl1 REFERENCING NEW AS n FOR EACH ROW INSERT INTO tbl2 VALUES (n.col1, n.col2)](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000931.html)
* Create a view:
  * [CREATE VIEW vw1 AS SELECT col2 FROM tbl](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000935.html)

# DCL

* Grant on a table:
  * [GRANT SELECT, INSERT ON TABLE tbl1 TO user](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000966.html)
* Grant execution on a stored procedure:
  * [GRANT EXECUTE ON PROCEDURE prc1(INT, DATE) TO USER jdoe](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0007699.html)
  * [GRANT EXECUTE ON SPECIFIC PROCEDURE mypr TO GROUP admins](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0007699.html)
* Revoke on a table:
  * [REVOKE DELETE ON TABLE mytable FROM recur](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000990.html)
 
 # DML

* Insert values on a table:
  * [INSERT INTO tbl3 VALUES (2, 'b')](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000970.html)
  * [INSERT INTO tbl3 VALUES (3, 'c'), (4, 'd'), (5, 'e') --Atomic](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000970.html)
* Insert certain columns:
  * [INSERT INTO tbl1 (col1) VALUES (6)](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000970.html)
* Insert values from a select:
  * [INSERT INTO tbl6 SELECT col1 FROM tbl1](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000970.html)
* Insert in temporary table:
  * [INSERT INTO session.tmp1 VALUES (1)](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000970.html)
* Update fields:
  * [UPDATE tbl3 SET col1 = 5, mycol2 = 'e' -–all table](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0001022.html)
  * [UPDATE tbl3 SET col2 = 'd' WHERE col1 = 7](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0001022.html)
* Merge (upsert):
  * [MERGE INTO tbl3 AS t USING (SELECT col1 FROM tbl1) s ON (t.col1 = s.col1) WHEN MATCHED THEN UPDATE SET col2 = 'X' WHEN NOT MATCHED THEN INSERT VALUES (10, 'X')](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0010873.html)
* Delete rows:
  * [DELETE FROM tbl1 --all table](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000939.html)
  * [DELETE FROM tbl1 WHERE col1 > 5](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000939.html)
* Export:
  * [EXPORT TO myfile OF DEL SELECT * FROM tbl1](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.cmd.doc/doc/r0008303.html)
* Import:
  * [IMPORT FROM myfile OF DEL INSERT INTO mytable1](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.cmd.doc/doc/r0008304.html)
* Cursor:
  * [DECLARE cur1 CURSOR FOR SELECT * FROM tbl1](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000937.html)
* Load:
  * [LOAD FROM myfile OF DEL INSERT INTO tbl1](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.cmd.doc/doc/r0008305.html)
  * [LOAD FROM cur1 OF CURSOR INSERT INTO tbl1](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.cmd.doc/doc/r0008305.html)
* Query the status of the load in a table:
  * [LOAD QUERY TABLE tbl1](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.cmd.doc/doc/r0002000.html)
* Set integrity:
  * [SET INTEGRITY FOR tbl1 IMMEDIATE CHECKED](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000998.html)
* Ingest:
  * [INGEST FROM FILE myfile FORMAT DELIMITED INSERT INTO tbl1](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.cmd.doc/doc/r0057198.html)
* Get the next value from a sequence:
  * VALUES [NEXT VALUE FOR seq](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0023464.html)
  * INSERT INTO tbl3 (col1) VALUES (NEXT VALUE FOR seq)

# TCL

* Commit changes:
  * [COMMIT](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000903.html)
* Create a savepoint:
  * [SAVEPOINT sp1 ON ROLLBACK RETAIN CURSORS](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0003271.html)
* Undo changes until savepoint:
  * [ROLLBACK TO SAVEPOINT sp1](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000992.html)
* Undo changes:
  * [ROLLBACK](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000992.html)

# Queries

* Put a lock at table level:
  * [LOCK TABLE tbl1 IN EXCLUSIVE MODE](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000972.html)
* Execute a query without regard of commit rows:
  * [SELECT * FROM tbl WITH UR --RR,RS,CS](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000993.html)
* Execute a query with only 5 rows:
  * [SELECT * FROM tbl1 FETCH FIRST 5 ROWS ONLY](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000879.html)
* Perform a query to a dummy table (dual):
  * SELECT 'Any string' FROM [SYSIBM.SYSDUMMY1](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0002369.html)
* Perform a query calling a function:
  * SELECT [HEX](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000811.html)(col2) FROM tbl5
* Call a function:
  * [VALUES HEX('AnyText')](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0001024.html)
* Perform a cast:
  * [VALUES CAST('123' AS INTEGER)](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0001024.html)
* Concatenate:
  * VALUES 'AnyText' || 5](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0001024.html)
  * VALUES 'AnyText' [concat](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0001024.html) 5
* Escape a single quote in a text field:
  * [VALUES 'Sinead o''Connor'](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0001024.html)
* Query the database catalog:
  * SELECT * FROM [SYSCAT.TABLES](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0001063.html)
  * SELECT * FROM [SYSCAT.TABAUTH](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0001061.html)
  * SELECT * FROM [SYSCAT.ROUTINES](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0001045.html)

# SQL PL

* Create a compound statement – Anonymous block:
  * [BEGIN DECLARE val SMALLINT; SET val = 1; WHILE (val &lt;= 5) DO INSERT INTO tbl5 VALUES (val, val); SET val = val + 1; END WHILE; END @](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0056580.html)
* Call a stored procedure with an IN and an OUTPUT parameter:
  * [CALL prc(5, ?)](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000897.html)
* Perform a reorg via ADMIN_CMD (Sometimes required after “alter table”):
  * CALL [SYSPROC.ADMIN_CMD](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.rtn.doc/doc/r0012547.html)('REORG TABLE tbl1')

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).
