## Querying Data

```

use Illuminate\Support\Facades\DB;

use with('relation-function-name') to get a relation with that query

$messages = Message::find(1);
$messages = Message::where('id', 1)->first();
$messages = Message::all();
$messages = Message::findOrFail(88);
$message = Message::find(1);
$message->author = "Sanjay PJ";
$message->save();
$messages = Message::all();
Message::destroy(1);
return ($messages);

$messages = DB::table('messages')->get();
$messages = DB::table('messages')->where('id', 1)->get();
$messages = DB::table('messages')->where('id', 1)->value('author');
$message = DB::table('messages')->find(1);
$messages = DB::table('messages')->pluck('body', 'author');
DB::table('messages')->orderBy('id')->chunk(2, function($messages){
  // return $messages;
});
$messages = DB::table('messages')->orderBy('author')->count();
$messages = DB::table('messages')->select('body', 'author')->groupBy('author')->get();
$messages = DB::table('messages')->where([
    ['author', '=', 'Sanjay PJ'],
    ['id', '=', 1],
])->get();
$messages = DB::table('messages')
                  ->where('id', '=', 1)
                  ->orWhere('author', 'Sanjay PJ')
                  ->get();
  $messages = DB::table('messages')->latest()->first();
  $messages = DB::table('messages')->insert(
    ['author' => 'john@example', 'body' => "Nulla in orci ut sapien tempor dignissim. Praesent auctor lobortis ornare. In commodo lobortis odio et interdum. Fusce vel tellus quis est ultrices condimentum at a urna. Nulla elementum justo sit amet orci pulvinar, vitae finibus nulla porta. Nulla maximus finibus tellus ac sodales. Ut fermentum augue eget lacus consequat, eget interdum libero fringilla."]
);
DB::table('messages')
          ->where('id', 1)
          ->update(["author" => "Sanjay P J"]);
DB::table('messages')->where('id', '=', 5)->delete();
$messages = DB::table('messages')->get();
$messages = DB::table('messages')->paginate(5);
$messages = DB::table('messages')->take(10)->get();

$body = "Suspendisse nec felis nisl. Sed dictum ut elit eget mollis. Aenean porttitor mi ante, et sagittis felis molestie et. Sed condimentum, neque ac euismod iaculis, orci eros sodales tellus, a suscipit eros massa id ligula. Duis aliquam nulla quam, accumsan fermentum sapien fermentum eu. Duis luctus est augue, et vulputate eros tristique sit amet. Donec ullamcorper sem quis venenatis mollis. Curabitur et lacus et nulla laoreet malesuada. Vestibulum eu libero quis massa facilisis rutrum. Quisque tincidunt commodo venenatis. Proin laoreet non purus sit amet commodo. Nam id velit nisl. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas.";
$messages = DB::select('select * from messages');
$messages = DB::select('select * from messages where author = ?', ["William"]);
$messages = DB::select('select * from messages where id = :id', ['id' => 1]);
$worked_or_not = DB::insert('insert into messages (body, author) values (?, ?)', [$body, 'Natalie Harrison']);
if($worked_or_not){
  $messages = DB::select('select * from messages');
  return $messages;
};
$updated_message = DB::update('update messages set author = ? where id = ?', ['Sanjay PJ', 1]);
$deleted = DB::delete('delete from messages where id = :id', ['id' => 2]);

```

[Ref: Query](https://laravel.com/docs/5.8/queries)