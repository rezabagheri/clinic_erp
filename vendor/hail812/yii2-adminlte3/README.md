hail812/yii2-adminlte3
======================
adminlte3 for yii2

![home](https://user-images.githubusercontent.com/3158261/80058324-8d751480-855b-11ea-87f5-3d682f787210.png)

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require --prefer-dist hail812/yii2-adminlte3 "~1.0.1"
```

or add

```
"hail812/yii2-adminlte3": "~1.0.1"
```

to the require section of your `composer.json` file.


Usage
-----

Once the extension is installed, you can config the path mappings of the view component:

```php
'components' => [
    'view' => [
         'theme' => [
             'pathMap' => [
                '@app/views' => '@vendor/hail812/yii2-adminlte3/src/views'
             ],
         ],
    ],
],
```

Copy files from @vendor/hail812/yii2-adminlte3/src/views to @app/views, then edit.

simply use:

```php
<?= \hail812\adminlte3\widgets\Alert::widget([
    'type' => 'success',
    'body' => '<h3>Congratulations!</h3>'
]) ?>
```

AdminLTE Plugins
----------------
AdminLTE Plugins are not included in AdminLteAsset, if you want to use any of them you can add it dynamically with PluginAsset.
For example:

```php
/* @var $this \yii\web\View */

\hail812\adminlte3\assets\PluginAsset::register($this)->add('sweetalert2');
```

before this, maybe you should edit params.php:

```php
return [
    'adminEmail' => 'admin@example.com',
    'hail812/yii2-adminlte3' => [
        'pluginMap' => [
            'sweetalert2' => [
                'css' => 'sweetalert2-theme-bootstrap-4/bootstrap-4.min.css',
                'js' => 'sweetalert2/sweetalert2.min.js'
            ]
        ]
    ]
];
```

or

```php
/* @var $this \yii\web\View */

$bundle = \hail812\adminlte3\assets\PluginAsset::register($this);
$bundle->css[] = 'sweetalert2-theme-bootstrap-4/bootstrap-4.min.css';
$bundle->js[] = 'sweetalert2/sweetalert2.min.js';
```