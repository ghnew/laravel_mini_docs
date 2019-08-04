## Faking data to Database

### Install faker library

```
composer require fzaninotto/faker --dev
```

### Creating Factory

```
php artisan make:factory PersonFactory
```

### Inside Factory File 

```
use Faker\Generator as Faker;
use App\Person;

$factory->define(person::class, function (Faker $faker) {
    return [
        'name' => $faker->name,
        'firstName' => $faker->firstName,
        'lastName' => $faker->lastName
    ];
});
```

### Creating Seeder

```
php artisan make:seeder PersonsTableSeeder
```

### Inside seeder file

```
use Illuminate\Database\Seeder;
use App\Person;

class PersonsTableSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        $count = 100;
        factory(Person::class, $count)->create();
    }
}
```


### Entry into DatabaseSeeder.php

```
use Illuminate\Database\Seeder;

class DatabaseSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
        $this->call(PersonsTableSeeder::class);
    }
}
```

### Seed into DB

```
php artisan db:seed
```