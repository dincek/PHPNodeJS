PHPNodeJS
=========

PHP Node JS wrapper - PHP class that brings JavaScript executing inside PHP - wrapper for NodeJS CLI.  
  
This class was made that we can use JavaScript based validators of tasks (interacitve tasks) for competition system Bober (programming competition). 
JavaScript server execution enables us to protect to correct solution for tasks.  
  
We think that this solution could be used for many other things so we published this wrapper online, so you can review it, test it and make it better.

Requirements
------------
- [NodeJS]("http://nodejs.org/", "NodeJS") (>= v0.10.10, maybe it works with older version (never tested, you are welcome to test and report if it works or not), there must be binary file "node" on server / computer where you execute script)
- If you want to use JavaScript function that uses jQuery you need to install jquery for NodeJS via NPM (in directory where 
PHPNodeJS.php is located in your project, you need to run command in CLI: `npm install jquery`

Installation
------------
For mac users no changes required, for windows users change this code on line 34
```
$this->NodePath = trim(shell_exec('which node'));
```
with this
```
$this->NodePath = trim(shell_exec('what node'));
```

Initialize
----------
```
include_once dirname(__FILE__) . '/PHPNodeJS.php';
// if $debug = true all of debug messages will be shown, otherwise not
$debug = true;
$PHPNodeJS = new PHPNodeJS($debug);
```

Example 1
--------
Run simple script without function
```
echo $PHPNodeJS->run('
  var var1 = 10;
  var var2 = 20;
  console.log(var1+var2);
');
```

Example 2 
---------
Run simple script, supply multiple arguments to function you want to call
```
echo $PHPNodeJS->run('
  function test(var1, var2) {
    if (var1 == "3" && var2 == "20") {
      return true;
    } else {
      return false;
    }
  }',
  'test', array('3', '20'));
```

Example 3
---------
Run script that uses jQuery as dependcy
```
echo $PHPNodeJS->run('
  function test(url) {
   jQuery.get(url, function(data) {
     console.log(data);
   });
   return "";
  }',
  'test', array('http://www.videodeck.net'), true);
```
License
-------
This project is licensed under [Creative Commons Attribution-ShareAlike 3.0 Unported (CC BY-SA 3.0)]("http://creativecommons.org/licenses/by-sa/3.0/", "CC BY-SA 3.0"). You are welcome to contribute to this project or 
fork this product but we would be very happy that you keep reference to this original project.
