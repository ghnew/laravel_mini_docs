## Models and Migrations

### Creating Models

```
php artisan make:model Flight
```

### Creating Migrations

```
php artisan make:migration create_users_table
```

[Ref: Create Migrations](https://laravel.com/docs/5.8/migrations)

### Redo all Migrations

```
php artisan migrate:fresh --seed
```

### Create both at same time

```
php artisan make:model Flight --migration
```

**Models can be found *app/***
**Migrations can be found *database/migrations/***

### One To One Relationship

```
public function phone()
{
    return $this->hasOne('App\Phone');
}
```

```
public function user()
{
    return $this->belongsTo('App\User');
}
```

### One To Many Relationship

```
public function comments()
{
    return $this->hasMany('App\Comment');
}
```

```
public function user()
{
    return $this->belongsTo('App\User');
}
```

### Many to Many

users, roles, and role_user. The role_user table is derived from the alphabetical order of the related model names, and contains the user_id and role_id columns.

```
public function roles()
{
    return $this->belongsToMany('App\Role');
}
```

```
public function users()
{
    return $this->belongsToMany('App\User');
}
```