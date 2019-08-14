## API

### add Routes here **routes/api.php**

```
//list articles
Route::get('articles', 'ArticleController@index');
//list single article
Route::get('article/{id}', 'ArticleController@show');
//create new article
Route::post('article', 'ArticleController@store');
//update article
Route::put('article', 'ArticleController@store');
//delete article
Route::delete('article/{id}', 'ArticleController@destroy');

```
### Make A Controller

```

use App\Http\Resources\Article as ArticleResource;

public function index()
{
    // get articles
    $articles = Article::paginate(15);
    //return collection of articles as a resource
    return ArticleResource::collection($articles);
}
/**
 * Show the form for creating a new resource.
 *
 * @return \Illuminate\Http\Response
 */
/**
 * Store a newly created resource in storage.
 *
 * @param  \Illuminate\Http\Request  $request
 * @return \Illuminate\Http\Response
 */
public function store(Request $request)
{
    $article = $request->isMethod('put') ? Article::findOrFail($request->article_id) : new Article;
    $article->id = $request->input('article_id');
    $article->title = $request->input('title');
    $article->body = $request->input('body');

    if($article->save()){
        return new ArticleResource($article);
    }
}
/**
 * Display the specified resource.
 *
 * @param  int  $id
 * @return \Illuminate\Http\Response
 */
public function show($id)
{
    // get article
    $article = Article::findOrFail($id);
    //return single article as resource
    return new ArticleResource($article);
}
/**
 * Remove the specified resource from storage.
 *
 * @param  int  $id
 * @return \Illuminate\Http\Response
 */
public function destroy($id)
{
    // get article
    $article = Article::findOrFail($id);
    if($article->delete()){
        return new ArticleResource($article);
    }
}

```
### Create resource using make:resource 
```
namespace App\Http\Resources;
use Illuminate\Http\Resources\Json\JsonResource;
class Article extends JsonResource
{
    /**
     * Transform the resource into an array.
     *
     * @param  \Illuminate\Http\Request  $request
     * @return array
     */
    public function toArray($request)
    {
        // return parent::toArray($request);
        return [
            'id' => $this->id,
            'title' => $this->title,
            'body' => $this->body
        ];
    }
    public function with($request){
        return [
            'version' => '1.0.0'
        ];
    }
}

```


#OR


```
Route::middleware('auth:api')->get('/user', function (Request $request) {
	return $request->user();
});

Route::get('contacts', function(){
	return Contact::orderBy('created_at','desc')->get();
});

Route::get('contact/{id}', function($id){
	return Contact::findOrFail($id);
});

Route::post('contact/store', function(Request $request){
	return Contact::create(['name' => $request->name, 'email' => $request->email, 'phone' => $request->email])
});

Route::patch('contact/{id}', function(Request $request, $id){
	return Contact::findOrFail($id)->update(['name' => $request->name, 'email' => $request->email, 'phone' => $request->phone])
});
```
