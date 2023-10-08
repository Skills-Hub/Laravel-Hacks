### Laravel Query Builder

#### What it is:
The Laravel Query Builder provides a convenient, fluent interface to creating and running database queries. It can be used to perform most database operations in your application and works on all supported database systems.

#### How it works:
1. **Fluent Interface**: The query builder offers a set of chainable methods that allow you to build queries piece by piece.
2. **Direct SQL**: It doesn't use the Eloquent ORM but instead builds raw SQL queries. However, it ensures that these queries are safe from SQL injection attacks.
3. **Multiple Database Support**: The query builder supports a wide range of database systems, including MySQL, PostgreSQL, SQLite, and SQL Server.

#### Why it's like that:
While Eloquent ORM provides a rich and convenient way to interact with databases, not every task or developer requires an ORM. The query builder is Laravel's solution to provide a direct but still elegant way of building and executing database queries.

#### When to use it:
1. **Fine-grained Control**: When you need more control over the SQL being executed.
2. **Simple Tasks**: For simple tasks where the overhead of an ORM isn't needed.
3. **No Model Relation**: For database tables that don't necessarily have a corresponding Eloquent model or relation.
4. **Data Manipulation**: For complex data manipulation tasks or when working with non-relational data structures.

#### Pros:
1. **Simplicity**: It bridges the gap between raw SQL and Eloquent, offering a more direct way of handling database interactions.
2. **Flexibility**: Allows for more complex and custom query structures.
3. **SQL Injection Protection**: Despite building raw SQL, the query builder protects against SQL injection attacks by using PDO parameter binding.
4. **Database Agnostic**: Like Eloquent, it supports multiple database backends.

#### Cons:
1. **Not Object-Oriented**: Doesn't return actual objects of a model. Instead, it returns a standard PHP `stdClass` object or an array.
2. **Lack of Eloquent Features**: Doesn't have Eloquent's features like eager loading, model events, or relationships.

#### Example:

Here's how you might use the Laravel Query Builder:

1. **Retrieve All Rows From A Table**:
   ```php
   use Illuminate\Support\Facades\DB;

   $users = DB::table('users')->get();
   ```

2. **Retrieve Specific Columns**:
   ```php
   $names = DB::table('users')->select('name')->get();
   ```

3. **Conditional Statements**:
   ```php
   $users = DB::table('users')->where('account_type', '=', 'admin')->get();
   ```

4. **Chaining Methods**:
   ```php
   $users = DB::table('users')
               ->where('account_type', '=', 'admin')
               ->orderBy('created_at', 'desc')
               ->take(10)
               ->get();
   ```

5. **Inserting Data**:
   ```php
   DB::table('users')->insert([
       'name' => 'John',
       'email' => 'john@example.com',
       'password' => bcrypt('secret')
   ]);
   ```

Laravel's Query Builder is a versatile tool, allowing for a more controlled and direct interaction with databases without the overhead of an ORM.
