## Validate POST Request

```
$validatedData = $request->validate([
    'title' => 'required|unique:posts|max:255',
    'body' => 'required',
]);
```

[Ref: Validation](https://laravel.com/docs/5.8/validation)