kint
====

kint yii extension


Requirements 

  Tested on 1.1.8. Should work on earlier versions.

Setup 

Download and extract the folder under protected/extensions.

Add to your config (main.php) under components:
~~~
'kint' => array(
    'class' => 'ext.Kint.Kint',
),
~~~

Add it to your preload property (this is only for declaring the shortcut functions):

~~~
'preload' => array('log', 'kint'),
~~~

Note: You can still use the plugin without autoloading, but instead of using the shortcut functions, you have to use:
~~~
Kint::dump($variable);
~~~
Usage:

To dump a variable:
~~~
d($variable);
~~~

There is often a need to halt execution after dumping a particular variable:
~~~
dd($variable); // execution will stop after this statement; same as d($variable);die;
~~~
To print out variable information in simple text (no CSS style or javascript) use
~~~
s($variable); // stands for "simple"
    // or, as before
  sd($variable); // this will halt execution after displaying data
~~~  

There are also (currently two) modifiers:
~~~
+d($variable); // will dump variable information without limiting the depth
    /// and
-d($variable); // will run ob_clean() beforehand, so this dump is at the top
                   // of the page. Best used with dd().
~~~                   
The latter are possible because the class analyzes the PHP code itself where it was called from.

Last, but not least, you can output a pretty and readable backtrace:

~~~
Kint::trace();
~~~
