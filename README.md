<h1>Welcome</h1>

<p>This is a wrapper for a PHP MySQL class, which utilizes MySQLi. This is inspired from CodeIgniter php framework. Most of the functions and documentations are identical to CodeIgniter database class and user guide and are extracted from it.</p>

<p>You do not need to use CodeIgniter to use this wrapper. Simply include the class file and you are good to go.</p>

<p>PHP 5.3 + MySQLi is required.</p>

<ul>
	<li><a href="#markdown-header-welcome">Welcome</a>

	<ul>
		<li><a href="#markdown-header-usage">Usage</a></li>
		<li><a href="#markdown-header-select-query">SELECT Query</a></li>
		<li><a href="#markdown-header-manual-db-query">Manual : $db-&gt;query()</a></li>
		<li><a href="#markdown-header-get-only-the-first-row-db-query_first">Get only the first row : $db-&gt;query_first()</a></li>
		<li><a href="#markdown-header-executing-query-db-execute">Executing Query : $db-&gt;execute()</a></li>
		<li><a href="#markdown-header-using-active-record-pattern">Using Active Record Pattern</a></li>
		<li><a href="#markdown-header-select-query-db-select-from">SELECT Query : $db-&gt;select()-&gt;from()</a></li>
		<li><a href="#markdown-header-distinct-db-distinct">DISTINCT : $db-&gt;distinct();</a></li>
		<li><a href="#markdown-header-from-clause-db-from">FROM clause : $db-&gt;from()</a></li>
		<li><a href="#markdown-header-where-clause-db-where">WHERE clause : $db-&gt;where()</a></li>
		<li><a href="#markdown-header-or_where-clause-db-or_where">OR_WHERE clause : $db-&gt;or_where()</a></li>
		<li><a href="#markdown-header-where-in-db-where_in">WHERE IN: $db-&gt;where_in()</a></li>
		<li><a href="#markdown-header-or-where-in-db-or_where_in">OR WHERE IN: $db-&gt;or_where_in()</a></li>
		<li><a href="#markdown-header-where-not-in-db-where_not_in">WHERE NOT IN : $db-&gt;where_not_in()</a></li>
		<li><a href="#markdown-header-or-where-not-in-db-or_where_not_in">OR WHERE NOT IN: $db-&gt;or_where_not_in()</a></li>
		<li><a href="#markdown-header-parenthesis-between-where">Parenthesis between WHERE</a></li>
		<li><a href="#markdown-header-select-from-where-execute">SELECT + FROM + WHERE + Execute</a></li>
		<li><a href="#markdown-header-fetching-the-result-db-fetch">Fetching the result : $db-&gt;fetch()</a></li>
		<li><a href="#markdown-header-fetching-the-first-row-db-fetch_first-or-db-fetch_result">Fetching the first row : $db-&gt;fetch_first() or $db-&gt;fetch_result()</a></li>
		<li><a href="#markdown-header-limit-and-offset-db-limit">LIMIT and OFFSET : $db-&gt;limit()</a></li>
		<li><a href="#markdown-header-get-db-get-from-version-151">GET : $db-&gt;get() ( from version 1.5.1)</a></li>
		<li><a href="#markdown-header-select_max-db-select_max">SELECT_MAX : $db-&gt;select_max()</a></li>
		<li><a href="#markdown-header-select_min-db-select_min">SELECT_MIN : $db-&gt;select_min()</a></li>
		<li><a href="#markdown-header-select_avg-db-select_avg">SELECT_AVG : $db-&gt;select_avg()</a></li>
		<li><a href="#markdown-header-select_sum-db-select_sum">SELECT_SUM : $db-&gt;select_sum()</a></li>
		<li><a href="#markdown-header-inserting-data-db-insert">Inserting Data : $db-&gt;insert()</a></li>
		<li><a href="#markdown-header-update-query-db-update">Update query : $db-&gt;update()</a></li>
		<li><a href="#markdown-header-last-query-db-last_query">Last Query : $db-&gt;last_query()</a></li>
		<li><a href="#markdown-header-dry-run-db-dryrun">Dry Run : $db-&gt;dryrun()</a></li>
		<li><a href="#markdown-header-escape-string-db-escape">Escape String : $db-&gt;escape()</a></li>
		<li><a href="#markdown-header-like-db-like">LIKE : $db-&gt;like()</a></li>
		<li><a href="#markdown-header-or-like-db-or_like">OR LIKE : $db-&gt;or_like()</a></li>
		<li><a href="#markdown-header-having-db-having">HAVING : $db-&gt;having()</a></li>
		<li><a href="#markdown-header-or-having-db-or_having">OR HAVING : $db-&gt;or_having()</a></li>
		<li><a href="#markdown-header-group-by-db-group_by">GROUP BY : $db-&gt;group_by()</a></li>
		<li><a href="#markdown-header-order-by-db-order_by">ORDER BY : $db-&gt;order_by()</a></li>
		<li><a href="#markdown-header-delete-db-delete">DELETE : $db-&gt;delete();</a></li>
		<li><a href="#markdown-header-dry-run-on-delete-query">Dry Run on DELETE query</a></li>
		<li><a href="#markdown-header-join-db-join">JOIN : $db-&gt;join();</a></li>
		<li><a href="#markdown-header-find_in_set-db-find_in_set-from-version-143">FIND_IN_SET : $db-&gt;find_in_set() ( from version 1.4.3)</a></li>
		<li><a href="#markdown-header-between-db-between-from-version-146">BETWEEN : $db-&gt;between() ( from version 1.4.6)</a></li>
	</ul>
	</li>
</ul>

<h2>Usage</h2>

<p>To use this class, import it to your project</p>

<pre>
&lt;?php

require_once &#39;class.database.php&#39; ;
</pre>

<p>Once the class file is included, initialize it</p>

<pre>
&lt;?php

$db = new Database($host, $username, $password, $database);
</pre>

<p>If your MySQL installation is using a non standard port, you can specify the port as</p>

<pre>
&lt;?php

$db = new Database($host, $username, $password, $database, $port);
</pre>

<p>If you are going to use a table prefix, you can assign it as</p>

<pre>
&lt;?php

$db-&gt;set_table_prefix(&#39;wp_&#39;); // Sets wp_ as table prefix
</pre>

<h2>SELECT Query</h2>

<p>A query string can be generated in two ways</p>

<ol>
	<li>Manual query</li>
	<li>Using active records</li>
</ol>

<h2>Manual : $db-&gt;query()</h2>

<pre>
&lt;?php

$sql = &quot;SELECT * FROM table&quot; ;
$db-&gt;query($sql) ;
</pre>

<h2>Get only the first row : $db-&gt;query_first()</h2>

<p>query_first() can be used to get the first row of the query.</p>

<pre>
&lt;?php

$db-&gt;query_first(&quot;SELECT * FROM table&quot;) ;
// Produces: SELECT * FROM table LIMIT 1 ;
</pre>

<h2>Executing Query : $db-&gt;execute()</h2>

<pre>
&lt;?php
$sql = &quot;SELECT * FROM table&quot; ;
$db-&gt;query($sql) ;
$db-&gt;execute(); 

// Also using method chaining

$sql = &quot;SELECT * FROM table&quot;;
$db-&gt;query($sql)-&gt;execute() ;

echo &quot;Affected Rows : &quot; . $db-&gt;affected_rows ;  // Outputs the affected rows
</pre>

<h2>Using Active Record Pattern</h2>

<h2>SELECT Query : $db-&gt;select()-&gt;from()</h2>

<p>The following function permits you to write the SELECT portion of your query</p>

<pre>
&lt;?php

$db-&gt;select(&#39;title, content, date&#39;);
// Produces: SELECT title, content, date

$db-&gt;select(&#39;*&#39;);
// Produces: SELECT *
</pre>

<p>If you do not call the select() method, &quot;SELECT *&quot; will be assumed. If no parameter is given, select() will assume *</p>

<h2>DISTINCT : $db-&gt;distinct();</h2>

<pre>
&lt;?php

$db-&gt;distinct();

// Produces: SELECT DISTINCT
</pre>

<h2>FROM clause : $db-&gt;from()</h2>

<pre>
&lt;?php

$db-&gt;from(&#39;table&#39;) ; // Set the table name
</pre>

<p>You can also chain the methods such as</p>

<pre>
&lt;?php

$db-&gt;select(&quot;id, email&quot;)-&gt;from(&#39;table&#39;) ;
// Produces : SELECT id, email FROM table
</pre>

<h2>WHERE clause : $db-&gt;where()</h2>

<p>The general syntax for where() is</p>

<pre>
&lt;?php 

$db-&gt;where(&#39;a&#39;, &#39;b&#39; ); 
$db-&gt;where(&#39;c&#39;, &#39;d&#39; ); 
</pre>

<p>You can also feed an array as</p>

<pre>
&lt;?php 

$db-&gt;where( array
          (&#39;a&#39; =&gt; &#39;b&#39;,
           &#39;c&#39; =&gt; &#39;d&#39;
) ;
</pre>

<pre>
&lt;?php

$where = array(
     &#39;name&#39; =&gt; &#39;test&#39;,
     &#39;email&#39; =&gt; &#39;email@example.com&#39;
);

$db-&gt;where($where);
// Produces: WHERE name = &#39;test&#39; AND email = &#39;email&#39; 
// Using method chaining

$db-&gt;select()-&gt;from(&#39;table&#39;)-&gt;where($where) ;
// Produces: SELECT * FROM table WHERE name = &#39;test&#39; AND email = &#39;email&#39; 

// You can also skip select() if you want. 
$db-&gt;from(&#39;table&#39;)-&gt;where($where) ;
// Produces: SELECT * FROM table WHERE name = &#39;test&#39; AND email = &#39;email&#39; 
</pre>

<h2>OR_WHERE clause : $db-&gt;or_where()</h2>

<pre>
&lt;?php
$db-&gt;where(&#39;name !=&#39;, $name);
$db-&gt;or_where(&#39;id &gt;&#39;, $id);

// Produces: WHERE name != &#39;Joe&#39; OR id &gt; 50
</pre>

<h2>WHERE IN: $db-&gt;where_in()</h2>

<p>Generates a WHERE field IN (&#39;item&#39;, &#39;item&#39;) SQL query joined with AND if appropriate</p>

<pre>
&lt;?php
$names = array(&#39;Frank&#39;, &#39;Todd&#39;, &#39;James&#39;);
$db-&gt;where_in(&#39;username&#39;, $names);
// Produces: WHERE username IN (&#39;Frank&#39;, &#39;Todd&#39;, &#39;James&#39;)
</pre>

<h2>OR WHERE IN: $db-&gt;or_where_in()</h2>

<p>Generates a WHERE field IN (&#39;item&#39;, &#39;item&#39;) SQL query joined with OR if appropriate</p>

<pre>
&lt;?php
$names = array(&#39;Frank&#39;, &#39;Todd&#39;, &#39;James&#39;);
$db-&gt;or_where_in(&#39;username&#39;, $names);
// Produces: OR username IN (&#39;Frank&#39;, &#39;Todd&#39;, &#39;James&#39;)
</pre>

<h2>WHERE NOT IN : $db-&gt;where_not_in()</h2>

<p>Generates a WHERE field NOT IN (&#39;item&#39;, &#39;item&#39;) SQL query joined with AND if appropriate</p>

<pre>
&lt;?php
$names = array(&#39;Frank&#39;, &#39;Todd&#39;, &#39;James&#39;);
$db-&gt;where_not_in(&#39;username&#39;, $names);
// Produces: WHERE username NOT IN (&#39;Frank&#39;, &#39;Todd&#39;, &#39;James&#39;)
</pre>

<h2>OR WHERE NOT IN: $db-&gt;or_where_not_in()</h2>

<p>Generates a WHERE field NOT IN (&#39;item&#39;, &#39;item&#39;) SQL query joined with OR if appropriate</p>

<pre>
&lt;?php
$names = array(&#39;Frank&#39;, &#39;Todd&#39;, &#39;James&#39;);
$db-&gt;or_where_not_in(&#39;username&#39;, $names);
// Produces: OR username NOT IN (&#39;Frank&#39;, &#39;Todd&#39;, &#39;James&#39;)
</pre>

<h2>Parenthesis between WHERE</h2>

<p>To open a parenthesis, use open_where() and to close use close_where()</p>

<pre>
&lt;?php
$db-&gt;select(&#39;column&#39;)-&gt;from(&#39;table&#39;);
$db-&gt;where(&#39;foo&#39;, 15);
$db-&gt;open_where();
$db-&gt;or_where(&#39;foo &lt;&#39;, 15);
$db-&gt;where(&#39;bar &gt;=&#39;, 15);
$db-&gt;close_where();

// Produces  SELECT `column` FROM `table` WHERE `foo` = 15 OR (`foo` &lt; 15 AND `bar` &gt;= 15) 
</pre>

<h2>SELECT + FROM + WHERE + Execute</h2>

<p>The following example combines all the function to get the result easily</p>

<pre>
&lt;?php

$db-&gt;select()-&gt;from(&#39;table&#39;)-&gt;where($where)-&gt;execute(); 
$affected = $db-&gt;affected_rows ; // Gets the total number of rows selected 

// Again, you can skip the select() method if you are selecting all fields (*)
$db-&gt;from(&#39;table&#39;)-&gt;where($where)-&gt;execute();
</pre>

<h2>Fetching the result : $db-&gt;fetch()</h2>

<p>The result will be output as associative array when the fetch() is called. You do not need to call execute() before you call fetch(). The functions execute() and fetch() acts like same. The former does not return data and the latter returns an array with the data. In both the cases, $db-&gt;affected_rows will be set.</p>

<pre>
&lt;?php


$rows = $db-&gt;from(&#39;table&#39;)-&gt;where($where)-&gt;fetch(); 
echo $db-&gt;affected_rows ; // Output the total number of selected rows 

foreach($rows as $row )
{
   var_dump($row);
}

// Or in short

$rows = $db-&gt;from(&#39;table&#39;)-&gt;fetch();
var_dump($rows);
// Produces: SELECT * FROM table
</pre>

<h2>Fetching the first row : $db-&gt;fetch_first() or $db-&gt;fetch_result()</h2>

<p>This function will return only the first row of the result</p>

<pre>
&lt;?php
$array = $db-&gt;from(&#39;table&#39;)-&gt;fetch_first() ;

// Produces SELECT * FROM table LIMIT 1
// Returns an array
</pre>

<h2>LIMIT and OFFSET : $db-&gt;limit()</h2>

<pre>
&lt;?php 

$db-&gt;limit(1); 

// Produces the limit part :  LIMIT 1

$db-&gt;limit(1,2);

// Produces the limit and offset : LIMIT 1,2 

// Example

$db-&gt;select()-&gt;from(&#39;table&#39;)-&gt;limit(1,5)-&gt;execute();

// Produces: SELECT * FROM table LIMIT 1, 5
</pre>

<h2>GET : $db-&gt;get() ( from version 1.5.1)</h2>

<p>Get function saves time by calling multiple functions at once.</p>

<pre>
$db-&gt;select(&#39;*&#39;)-&gt;from(&#39;table&#39;)-&gt;fetch();
</pre>

<p>The same code can be expressed using</p>

<pre>
$db-&gt;get(&#39;table&#39;);
</pre>

<p>Get also takes Limit as the second parameter and Offset as the third parameter. These parameters are optional.</p>

<p><code>$db-&gt;select(&#39;*&#39;)-&gt;from(&#39;table&#39;)-&gt;limit(1,2)-&gt;fetch();</code></p>

<p>is equivalent to</p>

<pre>
$db-&gt;get(&#39;table&#39;, 1, 2);
</pre>

<h2>SELECT_MAX : $db-&gt;select_max()</h2>

<p>Writes a &quot;SELECT MAX(field)&quot; portion for your query. You can optionally include a second parameter to rename the resulting field.</p>

<pre>
&lt;?php
$result = $db-&gt;select_max(&#39;age&#39;)-&gt;from(&#39;table&#39;)-&gt;fetch();

// Produces: SELECT MAX(age) AS age FROM members

$result = $db-&gt;select_max(&#39;age&#39;, &#39;member_age&#39;)-&gt;from(&#39;table&#39;)-&gt;fetch();;

// Produces: SELECT MAX(age) AS member_age FROM members
</pre>

<h2>SELECT_MIN : $db-&gt;select_min()</h2>

<p>Writes a &quot;SELECT MIN(field)&quot; portion for your query. As with select_max(), You can optionally include a second parameter to rename the resulting field.</p>

<pre>
&lt;?php
$result = $db-&gt;select_min(&#39;age&#39;)-&gt;from(&#39;table&#39;)-&gt;fetch();

// Produces: SELECT MIN(age) AS age FROM members

$result = $db-&gt;select_min(&#39;age&#39;, &#39;member_age&#39;)-&gt;from(&#39;table&#39;)-&gt;fetch();;

// Produces: SELECT MIN(age) AS member_age FROM members
</pre>

<h2>SELECT_AVG : $db-&gt;select_avg()</h2>

<p>Writes a &quot;SELECT AVG(field)&quot; portion for your query. As with select_max(), You can optionally include a second parameter to rename the resulting field.</p>

<pre>
&lt;?php
$result = $db-&gt;select_avg(&#39;age&#39;)-&gt;from(&#39;table&#39;)-&gt;fetch();

// Produces: SELECT AVG(age) AS age FROM members

$result = $db-&gt;select_avg(&#39;age&#39;, &#39;member_age&#39;)-&gt;from(&#39;table&#39;)-&gt;fetch();;

// Produces: SELECT AVG(age) AS member_age FROM members
</pre>

<h2>SELECT_SUM : $db-&gt;select_sum()</h2>

<p>Writes a &quot;SELECT SUM(field)&quot; portion for your query. As with select_max(), You can optionally include a second parameter to rename the resulting field.</p>

<pre>
&lt;?php
$result = $db-&gt;select_sum(&#39;age&#39;)-&gt;from(&#39;table&#39;)-&gt;fetch();

// Produces: SELECT SUM(age) AS age FROM members

$result = $db-&gt;select_sum(&#39;age&#39;, &#39;member_age&#39;)-&gt;from(&#39;table&#39;)-&gt;fetch();;

// Produces: SELECT SUM(age) AS member_age FROM members
</pre>

<h2>Inserting Data : $db-&gt;insert()</h2>

<pre>
&lt;?php

$data = array(
    &#39;title&#39; =&gt; &#39;Some title&#39;,
    &#39;email&#39; =&gt; &#39;email@example.com&#39;, 
    &#39;created&#39; =&gt; &#39;NOW()&#39;

);

$id = $db-&gt;insert(&#39;tableName&#39;, $data) ; // $id will have the auto-increment 

echo &quot;Data inserted. ID:&quot; . $id ;
</pre>

<h2>Update query : $db-&gt;update()</h2>

<p>update() method can be used to update a table with the data. Update() expects that you already set the WHERE clause and LIMIT before calling update().</p>

<pre>
&lt;?php

$where = array(
         &#39;email&#39; = &gt; &#39;test@test.com&#39;,
         &#39;id&#39; =&gt; 14
);

$data = array(
         &#39;email&#39; =&gt; &#39;new@example.com&#39;,
         &#39;password&#39; =&gt; &#39;pass1&#39;
);

$db-&gt;where($where)-&gt;update(&#39;table&#39;, $data); 

// Produces: UPDATE table SET email = &#39;new@example.com&#39;, password = &#39;pass1&#39; WHERE email = &#39;test@test.com&#39; AND id = &#39;14&#39; ;

// NOTE: where() should be called BEFORE update(), otherwise it will be ignored. 

// You can also use or_where()

$db-&gt;or_where($where)-&gt;update(&#39;table&#39;, $data); 
// Produces: UPDATE table SET email = &#39;new@example.com&#39;, password = &#39;pass1&#39; WHERE email = &#39;test@test.com&#39; OR id = &#39;14&#39; ;
</pre>

<h2>Last Query : $db-&gt;last_query()</h2>

<p>This function will return the last generated query string. Useful for debugging purpose.</p>

<pre>
&lt;?php

$this-&gt;select(&#39;id&#39;)-&gt;from(&#39;table&#39;)-&gt;where(&#39;name&#39;, &#39;test&#39;)-&gt;execute();
echo $db-&gt;last_query();

// Produces: SELECT id FROM table where name = &#39;test&#39; ;
</pre>

<h2>Dry Run : $db-&gt;dryrun()</h2>

<p>Dry run will output the query string which is ready to be executed. If you call dryrun() then the query will not be executed. And the last_query() will output the query which is ready to be executed.</p>

<p>This function is often useful in case of calling DELETE or UPDATE function. The developer can view the DELETE or UPDATE query generated, before executing it.</p>

<pre>
&lt;?php
$data[&#39;email&#39;] = &#39;db@example.com&#39;;

echo $db-&gt;dryrun()-&gt;update(&#39;table&#39;, $data)-&gt;last_query();

// Produces: UPDATE table SET email = &#39;db@example.com&#39; , and the query is NOT executed. 
</pre>

<h2>Escape String : $db-&gt;escape()</h2>

<p>This function returns sanitized data for mysql operation</p>

<pre>
&lt;?php

$string = &quot;where &#39;s a and &#39;s&quot; ;
echo $db-&gt;escape($string);

// Produces: where \&#39;s a and \&#39;s
</pre>

<h2>LIKE : $db-&gt;like()</h2>

<p>This function enables you to generate LIKE clauses, useful for doing searches.</p>

<p>Simple key/value method:</p>

<pre>
&lt;?php

$db-&gt;like(&#39;title&#39;, &#39;match&#39;);

// Produces: WHERE title LIKE &#39;%match%&#39; 
</pre>

<p>If you use multiple function calls they will be chained together with AND between them:</p>

<pre>
&lt;?php

$db-&gt;like(&#39;title&#39;, &#39;match&#39;);
$db-&gt;like(&#39;body&#39;, &#39;match&#39;);

// WHERE title LIKE &#39;%match%&#39; AND body LIKE &#39;%match%
</pre>

<p>If you want to control where the wildcard (%) is placed, you can use an optional third argument. Your options are &#39;before&#39;, &#39;after&#39; and &#39;both&#39; (which is the default).</p>

<pre>
&lt;?php

$db-&gt;like(&#39;title&#39;, &#39;match&#39;, &#39;before&#39;);
// Produces: WHERE title LIKE &#39;%match&#39;

$db-&gt;like(&#39;title&#39;, &#39;match&#39;, &#39;after&#39;);
// Produces: WHERE title LIKE &#39;match%&#39;

$db-&gt;like(&#39;title&#39;, &#39;match&#39;, &#39;both&#39;);
// Produces: WHERE title LIKE &#39;%match%&#39; 
</pre>

<p>If you do not want to use the wildcard (%) you can pass to the optional third argument the option &#39;none&#39;.</p>

<pre>
&lt;?php

$db-&gt;like(&#39;title&#39;, &#39;match&#39;, &#39;none&#39;);
// Produces: WHERE title LIKE &#39;match&#39; 
</pre>

<p>Associative array method</p>

<pre>
&lt;?php

$array = array(&#39;title&#39; =&gt; $match, &#39;page1&#39; =&gt; $match, &#39;page2&#39; =&gt; $match);

$db-&gt;like($array);

// WHERE title LIKE &#39;%match%&#39; AND page1 LIKE &#39;%match%&#39; AND page2 LIKE &#39;%match%&#39;
</pre>

<h2>OR LIKE : $db-&gt;or_like()</h2>

<p>This function is identical to the one above, except that multiple instances are joined by OR:</p>

<pre>
&lt;?php
$db-&gt;like(&#39;title&#39;, &#39;match&#39;);
$db-&gt;or_like(&#39;body&#39;, $match);

// WHERE title LIKE &#39;%match%&#39; OR body LIKE &#39;%match%&#39;
</pre>

<h2>HAVING : $db-&gt;having()</h2>

<p>Permits you to write the HAVING portion of your query. There are 2 possible syntaxes, 1 argument or 2:</p>

<pre>
&lt;?php
$db-&gt;having(&#39;user_id = 45&#39;);
// Produces: HAVING user_id = 45

$db-&gt;having(&#39;user_id&#39;, 45);
// Produces: HAVING user_id = 45
</pre>

<p>You can also pass an array of multiple values as well:</p>

<pre>
&lt;?php
$db-&gt;having(array(&#39;title =&#39; =&gt; &#39;My Title&#39;, &#39;id &lt;&#39; =&gt; $id));

// Produces: HAVING title = &#39;My Title&#39;, id &lt; 45
</pre>

<h2>OR HAVING : $db-&gt;or_having()</h2>

<p>Identical to having(), only separates multiple clauses with &quot;OR&quot;.</p>

<h2>GROUP BY : $db-&gt;group_by()</h2>

<p>Permits you to write the GROUP BY portion of your query:</p>

<pre>
&lt;?php
$db-&gt;group_by(&quot;title&quot;);

// Produces: GROUP BY title 
</pre>

<p>You can also pass an array of multiple values as well:</p>

<pre>
&lt;?php
$db-&gt;group_by(array(&quot;title&quot;, &quot;date&quot;));

// Produces: GROUP BY title, date
</pre>

<h2>ORDER BY : $db-&gt;order_by()</h2>

<p>Lets you set an ORDER BY clause. The first parameter contains the name of the column you would like to order by. The second parameter lets you set the direction of the result. Options are asc or desc ( case insensitive)</p>

<pre>
&lt;?php
$db-&gt;order_by(&quot;title&quot;, &quot;desc&quot;);

// Produces: ORDER BY title DESC 
</pre>

<p>You can also pass your own string in the first parameter:</p>

<pre>
&lt;?php
$db-&gt;order_by(&#39;title desc, name asc&#39;);

// Produces: ORDER BY title desc, name asc
</pre>

<p>Or multiple function calls can be made if you need multiple fields.</p>

<pre>
&lt;?php
$db-&gt;order_by(&quot;title&quot;, &quot;desc&quot;);
$db-&gt;order_by(&quot;name&quot;, &quot;asc&quot;);

// Produces: ORDER BY title DESC, name ASC 
</pre>

<p>In addition to this, you can also use an array for multiple calls</p>

<pre>
&lt;?php
$order_by = array(&#39;title&#39; =&gt; &#39;desc&#39;,
                  &#39;name&#39;  =&gt; &#39;asc&#39;
);

$db-&gt;order_by($order_by);

// Produces: ORDER BY title DESC, name ASC 
</pre>

<h2>DELETE : $db-&gt;delete();</h2>

<p>Permits you to write DELETE statement. Delete function takes one optional argument - table. Also note that delete() requires that you call execute() at the end to execute the query</p>

<pre>
&lt;?php

$db-&gt;delete(&#39;table&#39;)-&gt;execute();

// Produces: DELETE FROM table
</pre>

<p>If table is not provided, it will take the table name set by &#39;$db-&gt;from()&#39; method</p>

<pre>
&lt;?php
$db-&gt;-&gt;delete()-&gt;from(&#39;table&#39;)-&gt;execute();

// Produces: DELETE FROM table
</pre>

<p>You can also use where(), limit(), having(), like() etc with delete method</p>

<pre>
&lt;?php

$db-&gt;delete()-&gt;from(&#39;table&#39;)-&gt;where(&#39;email&#39;, &#39;test@example.com&#39;)-&gt;limit(1)-&gt;execute();

// Produces: DELETE FROM table WHERE email = &#39;test@example.com&#39; LIMIT 1
</pre>

<p>delete() will also gives you the total number of rows deleted.</p>

<pre>
&lt;?php

$db-&gt;delete()-&gt;from(&#39;table&#39;)-&gt;execute();
echo &quot;Deleted Rows: &quot; . $db-&gt;affected_rows ;
</pre>

<h2>Dry Run on DELETE query</h2>

<p>Delete is a dangerous query which will irreversibly delete your data from the table. If you are not sure how the delete query will be generated, you can run dryrun() and it will give you the generated query which is ready to be executed.</p>

<pre>
&lt;?php

$db-&gt;dryrun()-&gt;delete(&#39;table&#39;)-&gt;exexute()-&gt;last_query();
// Outputs DELETE FROM table , but does not execute the query 
</pre>

<h2>JOIN : $db-&gt;join();</h2>

<p>Permits you to write JOIN statement.</p>

<pre>
&lt;?php
$db-&gt;select(&#39;*&#39;);
$db-&gt;from(&#39;blogs&#39;);
$db-&gt;join(&#39;comments&#39;, &#39;comments.id = blogs.id&#39;);


// Produces:
// SELECT * FROM blogs
// JOIN comments ON comments.id = blogs.id
</pre>

<p>Multiple function calls can be made if you need several joins in one query. If you need a specific type of JOIN you can specify it via the third parameter of the function. Options are: left, right, outer, inner, left outer, and right outer.</p>

<pre>
&lt;?php
$db-&gt;join(&#39;comments&#39;, &#39;comments.id = blogs.id&#39;, &#39;left&#39;);

// Produces: LEFT JOIN comments ON comments.id = blogs.id
</pre>

<h2>FIND_IN_SET : $db-&gt;find_in_set() ( from version 1.4.3)</h2>

<p>Generates a FIND_IN_SET query. Takes 3 parameters. First parameter is the string to find. Second parameter is the column name to search, and third parameter which is optional, will take an operator AND or OR to join multiple WHERE clauses.</p>

<pre>
&lt;?php
$db-&gt;find_in_set(&#39;503&#39;, &#39;orders&#39;)-&gt;from(&#39;tblinvoices&#39;)-&gt;fetch();
// Produces: SELECT *  FROM tblinvoices  WHERE  FIND_IN_SET (&#39;305&#39;, orders) 

$db-&gt;where(&#39;id&#39;, 5)-&gt;find_in_set(&#39;503&#39;, &#39;orders&#39;)-&gt;from(&#39;tblinvoices&#39;)-&gt;fetch();
// Produces: SELECT *  FROM tblinvoices WHERE id=&#39;5&#39; AND  FIND_IN_SET (&#39;305&#39;, orders) 

$db-&gt;where(&#39;id&#39;, 5)-&gt;find_in_set(&#39;503&#39;, &#39;orders&#39;, &#39;OR&#39;)-&gt;from(&#39;tblinvoices&#39;)-&gt;fetch();
// Produces: SELECT *  FROM tblinvoices WHERE id=&#39;5&#39; OR  FIND_IN_SET (&#39;305&#39;, orders) 
</pre>

<h2>BETWEEN : $db-&gt;between() ( from version 1.4.6)</h2>

<p>Generates a BETWEEN condition.</p>

<pre>
&lt;?php
$db-&gt;between(&#39;created&#39;, &#39;2014-05-05&#39;, &#39;2014-05-10&#39;);

// Produces: created BETWEEN &#39;2014-05-05&#39; AND &#39;2014-05-10&#39;

$db-&gt;from(&#39;tblinvoices&#39;)-&gt;where(&#39;clientid&#39;, &#39;12&#39;)-&gt;between(&#39;created&#39;, &#39;2014-05-05&#39; , &#39;2014-05-10&#39;)-&gt;fetch();

// Produces: SELECT * FROM tblinvoices WHERE clientid = &#39;12&#39; AND created BETWEEN &#39;2014-05-05&#39; AND &#39;2014-05-10&#39;</pre>
