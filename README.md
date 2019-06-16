# Laravel Helper Documents
## Instalation
### With xampp and composer
	1. https://getcomposer.org/ -> to donwnload composer
		- https://packagist.org -> to download composer packages
	2. Install composer to php.exe root
	3. **Run cmd and type** composer
	4. **type**  composer create-project --prefer-dist laravel/laravel project_name
	5. Run terminal
	6. **type** php artisan serve
		- This command will start a development server at http://localhost:8000:
### With laragon
	1. https://laragon.org/download/index.html -> to download laragon
	2. Install laragon
	3. Menu > Quick app > Laravel
	4. Give your desired project name
	
**hints**

	1. you may need to install and configur **phpmyadmin**. 
	2. Download phpmyadmin and extract here **laragon\etc\apps**
	
### Route
**Location** routes/web.php
```
Route::get('/', 'PagesController@home');
Route::get('/contact', function () {
	return view('contact');
});
Route::post('/login/custom',[
	'uses' => 'LoginController@login',
	'as' => 'login.custom',
]);
```
**Resource**
```
Route::resource('projects','ProjectsController');

// Route::get('/projects', 'ProjectsController@index');
// Route::post('/projects', 'ProjectsController@store');
// Route::get('/projects/create', 'ProjectsController@create');
// Route::get('/projects/{project}', 'ProjectsController@show');
// Route::patch('/projects/{project}', 'ProjectsController@update');
// Route::delete('/projects/{project}', 'ProjectsController@destroy');
// Route::get('/projects/{project}/edit', 'ProjectsController@edit');
```
**Available Router Methods**
```
Route::get($uri, $callback);
Route::post($uri, $callback);
Route::put($uri, $callback);
Route::patch($uri, $callback);
Route::delete($uri, $callback);
Route::options($uri, $callback);
```
**a route that responds to multiple HTTP verbs**
```
Route::match(['get', 'post'], '/', $callback);
Route::any('/', $callback);
```
**View Routes**
```
Route::view('/welcome', 'welcome');
Route::view('/welcome', 'welcome', ['name' => 'Taylor']);
```
**Optional Parameters**
```
Route::view('/welcome/{name?}', 'welcome');
```
### Controllers
**Location** App/Http/Controllers

**Create** 

	1. php artisan help make:controller
	2. php artisan make:controller ControllerName
	3. php artisan make:controller --resource ControllerName 
	
### View
	1. return view('welcome');
		- return welcome.blade.php from view directory
	2. return view('admin.welcome');
		- return welcome.blade.php from view/admin directory
	3. return view('admin/welcome');
		- return welcome.blade.php from view/admin directory
		
**Passing info to view**
	1. return view('welcome',['tasks' => $tasks,'foo' => 'Foobar','request' => request('title'),'script' => '<script>alert("Foobar")</script>']);
	2. return view('welcome', compact('id', 'name', 'password'));
	3. return view('welcome')->with('name', $value);
	4. return view('welcome')->with(['foo' => 'Foobar','tasks' => ['Go to the store','Go to the market',],]);
	5. return view('welcome')->withTasks($tasks)->withFoo('foo');