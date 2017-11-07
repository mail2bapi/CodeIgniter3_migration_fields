# CodeIgniter3_migration_fields
Expanding CodeIgniter 3 migration feature. Adding fields made easy to migration file. At present it only support MYSQL database.

## Installation
Download and drag the Migrationfields.php file into your **application/libraries** directory.

## How to use it
Create a migration file in **application/migrations/** directory as instructed in CI 3 [documentation](https://www.codeigniter.com/user_guide/libraries/migration.html).

You can follow the example to add your fields to table easily.
```php
class Migration_Add_person extends CI_Migration
{
    public function up()
    {
        $this->load->library('migrationfields');

        $this->migrationfields->setTableName('person')
            ->increments('id')->primary()
            ->char('first_name', 100)
            ->char('middle_name', 100)->null()
            ->char('email', 100)->unique()
            ->integer('age', 3, 0)
            ->date('dob')->index()
            ->migrate();
    }

    public function down()
    {
        $this->dbforge->drop_table('person');
    }
}
```

## Available methods

### migrate
Execute the migration and create table and fields

### primary
Make the field primary. It is after field defination.
***Parameters*** 
+ No parameters need

***Return*** 
+ Doesn't return anything

```php
increments('id')->primary()
```

### index
Behave same as primary method. But only do index on the field.

***Parameters*** 
+ No parameters need

***Return*** 
+ Doesn't return anything

### unique
Behave same as primary method. But only do unique on the field.

***Parameters*** 
+ No parameters need

***Return*** 
+ Doesn't return anything

### null
Allow the field to have null value

***Parameters*** 
+ No parameters need

***Return*** 
+ Doesn't return anything

### increments
It is a field that is unsigned interger having constraint of 10. It is generally used for primary key with AUTO_INCREMENT.

***Parameters*** 
+ string $fieldName - Name of the field
+ int $size - constraint

***Return*** 
+ Doesn't return anything

### integer
Make field integer

***Parameters*** 
+ string $fieldName - Name of the field
+ int $size - constraint
+ string $default - default value for the field. By default set to **0**
+ bool $unsigned - make the field signed (false) or unsigned (true). By default set to **true**

***Return*** 
+ Doesn't return anything

### decimal
Make field decimal

***Parameters*** 
+ string $fieldName - Name of the field
+ int $size - whole-number part
+ int $scale - fractional part
+ string $default - default value for the field. By default set to **0**
+ bool $unsigned - make the field signed (false) or unsigned (true). By default set to **true**

***Return*** 
+ Doesn't return anything

### float
Make field float

***Parameters*** 
+ string $fieldName - Name of the field
+ int $size - whole-number part
+ int $scale - fractional part
+ string $default - default value for the field. By default set to **0**
+ bool $unsigned - make the field signed (false) or unsigned (true). By default set to **true**

***Return*** 
+ Doesn't return anything

### boolean
Integet field act as boolean. 0 is equal to false and 1 is equal to true.

***Parameters*** 
+ string $fieldName - Name of the field
+ string $default - default value for the field. By default set to **false**

***Return*** 
+ Doesn't return anything

### char
Make field varchar

***Parameters*** 
+ string $fieldName - Name of the field
+ int $size - constraint
+ string $default - default value for the field. 

***Return*** 
+ Doesn't return anything

### text
Make field text

***Parameters*** 
+ string $fieldName - Name of the field

***Return*** 
+ Doesn't return anything

### date
Make field date

***Parameters*** 
+ string $fieldName - Name of the field
+ string $default - default value for the field. By default set to **0000-00-00**

***Return*** 
+ Doesn't return anything

### dateTime
Make field datetime

***Parameters*** 
+ string $fieldName - Name of the field
+ string $default - default value for the field. By default set to **0000-00-00**

***Return*** 
+ Doesn't return anything

### setTableName
Take a table name

***Parameters*** 
+ string $tableName

***Return*** 
+ Doesn't return anything

### setStorageEngine
Define MYSQL engine type

***Parameters*** 
+ string $storageEngine - Define MYSQL engine type. By default set to **InnoDB**

***Return*** 
+ Doesn't return anything

### setCharset
Set charset for the table

***Parameters*** 
+ string $charset - By default set to **uft8**

***Return*** 
+ Doesn't return anything

### setCollation 
Set collation for the table

***Parameters*** 
+ string $collation - By default set to **utf8_unicode_ci**

***Return*** 
+ Doesn't return anything


Enjoy using my MCodeIgniter3_migration_fields and please report any issues you find or try some pull requests. Thank you!
