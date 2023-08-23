# Laravel 10.x Release Notes

- Laravel 10.x required a minimum PHP version of 8.1.
- Recent past many new features have been added to PHP in the subsequent year, including additional type-hints,return types, and union types. Laravel 10.x throughly updates the application skeleton and all stubs utilized by the framework based on the PHP changes.
- Laravel Pennant. It is kind of features management tools. Like as mini RBAC.
- Process Interaction. The new package introduce with laravel 10.x is Process. Which is mainly used to execute shell command inside the application.
- Test Profiling. Add time of execution of each test in the terminal. Now you can see which test case is slowest in your application.
- Update Horizon/Telescope UI

## Laravel 10.19
 - Word wrap string method. It splitis string within a string using character limit.
    

        Str::wordWrap(string: $text, characters: 8); 
    
 - Add percentage method to collections. You can calculate a percentage of the collection based on custom logic.
       

        $collection = new $collection([
            ['name' => 'Taylor', 'foo' => 'foo'],
            ['name' => 'Nuno', 'foo' => 'bar'],
            ['name' => 'Dries', 'foo' => 'bar'],
            ['name' => 'Jess', 'foo' => 'baz'],
        ]);
        $collection->percentage(fn ($value) => $value['foo'] === 'foo'); // 25.00
    

## Laravel 10.19
 - toRawSql, dumpRawSql, ddRawSql