Imperavi Redactor Widget for Yii 2
==================================

`Imperavi Redactor Widget` is a wrapper for [Imperavi Redactor](http://imperavi.com/redactor/),
a high quality WYSIWYG editor.

Note that Imperavi Redactor itself is a proprietary commercial copyrighted software
but since Yii community bought OEM license you can use it for free with Yii.

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require --prefer-dist vova07/yii2-imperavi-widget "*"
```

or add

```
"vova07/yii2-imperavi-widget": "*"
```

to the require section of your `composer.json` file.


Usage
-----

Once the extension is installed, simply use it in your code:

### Like a widget ###

```php
echo \vova07\imperavi\Widget::widget([
    'settings' => [
        'lang' => 'ru',
        'minHeight' => 200,
        'pastePlainText' => true,
        'plugins' => [
            'clips',
            'fullscreen'
        ]
    ]
]);
```

### Like an AtiveForm widget ###

```php
use vova07\imperavi\Widget;

echo $form->field($model, 'content')->widget(Widget::className(), [
    'settings' => [
        'lang' => 'ru',
        'minHeight' => 200,
        'pastePlainText' => true,
        'plugins' => [
            'clips',
            'fullscreen'
        ]
    ]
]);
```

### Like a widget for a predefined textarea ###

```php
echo \vova07\imperavi\Widget::widget([
    'selector' => '#my-textarea-id',
    'settings' => [
        'lang' => 'ru',
        'minHeight' => 200,
        'pastePlainText' => true,
        'plugins' => [
            'clips',
            'fullscreen'
        ]
    ]
]);
```

### Add files that have already been uploaded ###

```php
// DefaultController.php
public function actions()
{
    return [
        'get' => [
            'class' => 'vova07\imperavi\actions\GetAction',
            'url' => 'http://my-site.com/images/', // Directory URL address, where files are stored.
            'path' => '@alias/to/my/path' // Or absolute path to directory where files are stored.
        ]
    ];
}

// View.php
echo \vova07\imperavi\Widget::widget([
    'selector' => '#my-textarea-id',
    'settings' => [
        'lang' => 'ru',
        'minHeight' => 200,
        'pastePlainText' => true,
        'plugins' => [
            'clips',
            'fullscreen'
        ],
        'imageGetJson' => Url::to(['/default/get'])
    ]
]);
```

### Upload image ###

```php
// DefaultController.php
public function actions()
{
    return [
        'image-upload' => [
            'class' => 'vova07\imperavi\actions\UploadAction',
            'url' => 'http://my-site.com/images/', // Directory URL address, where files are stored.
            'path' => '@alias/to/my/path' // Or absolute path to directory where files are stored.
        ],
    ];
}

// View.php
echo \vova07\imperavi\Widget::widget([
    'selector' => '#my-textarea-id',
    'settings' => [
        'lang' => 'ru',
        'minHeight' => 200,
        'pastePlainText' => true,
        'plugins' => [
            'clips',
            'fullscreen'
        ],
        'imageUpload' => Url::to(['/default/image-upload'])
    ]
]);
```

### File image ###

```php
// DefaultController.php
public function actions()
{
    return [
        'file-upload' => [
            'class' => 'vova07\imperavi\actions\UploadAction',
            'url' => 'http://my-site.com/images/', // Directory URL address, where files are stored.
            'path' => '@alias/to/my/path' // Or absolute path to directory where files are stored.
        ],
    ];
}

// View.php
echo \vova07\imperavi\Widget::widget([
    'selector' => '#my-textarea-id',
    'settings' => [
        'lang' => 'ru',
        'minHeight' => 200,
        'pastePlainText' => true,
        'plugins' => [
            'clips',
            'fullscreen'
        ],
        'fileUpload' => Url::to(['/default/file-upload'])
    ]
]);
```