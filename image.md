## Upload Images

```
$request->validate([
    'title' => 'required',
    'photo' => 'required|image|max:1999'
]);
$file_name_with_ext = $request->file('photo')->getClientOriginalName();
$file_name = pathinfo($file_name_with_ext, PATHINFO_FILENAME);
$extension = $request->file('photo')->getClientOriginalExtension();
$file_name_to_store = $file_name . '_' . time() .  '.' . $extension;
$path = $request->file('photo')->storeAs('public/photos/' .  $request->input('album_id'), $file_name_to_store);
//creating album
$photo = new Photo;
$photo->album_id = $request->input('album_id');
$photo->title = $request->input('title');
$photo->description = $request->input('description');
$photo->size = $request->file('photo')->getClientSize();
$photo->photo = $file_name_to_store;
$photo->save();
```