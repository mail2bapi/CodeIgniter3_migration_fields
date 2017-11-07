# CodeIgniter3_migration_fields
Expanding CodeIgniter 3 migration feature. Adding fields made easy for MYSQL database.

## Installation
Download and drag the Migrationfields.php file into your **application/libraries** directory.

## How to use it
Create a migration file in **application/migrations/** directory as instructed in CI 3 [documentation](https://www.codeigniter.com/user_guide/libraries/migration.html).

You can follow the example to add you fields easily.
```php
class Migration_Add_patient extends CI_Migration
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
