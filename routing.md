
## Routes and controllers

### Make Controller Command

```
php artisan make:controller ControllerName
```
**Controller can be found */app/Http/Controllers***
**Views can be found *resources/views/***
**Views can be found *resources/views/***

```
php artisan make:controller ControllerName --resource
```

**this will create controller with urls and functions for a specific model**

### Controller functions and passing variables

```
public function index(){
    return view('templateName')->with([
        "categories"=> "something",
    ]);
}
```

### Implementing different types of Routes

```
Route::get('/uri', 'ControllerName@functionName');
Route::post('/uri', 'ControllerName@functionName');
Route::delete('/uri', 'ControllerName@functionName');
```
**Routes can be added *routes/web.php***
**there is a lot available but this is what you use almost everytime**

```
Route::redirect('/here', '/there', 301);
```
**Redirect route**

### Parameter passing through routes

```
Route::get('user/{id}', function ($id) {
    return 'User '.$id;
});
```
