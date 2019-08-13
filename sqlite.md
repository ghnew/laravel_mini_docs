## Setup SQLite

Step 1 - Create `database.sqlite` inside `database` folder.

Step 2 - Edit `'default' => env('DB_CONNECTION', 'mysql')` into `'default' => env('DB_CONNECTION', 'sqlite'),` in `config/database.php`

Step 3 - Edit `.env` file into sqlite and remove other properties related to database