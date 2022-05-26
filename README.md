# submodule-a
An use case of submodules in Git

This repo is the Containers of Submodules.

Further more, this repo is a framework according Composer configuration type.

I will follow steps from
https://git-scm.com/book/es/v2/Herramientas-de-Git-Subm%C3%B3dulos

```sh
$ git clone https://github.com/jagarsoft/submodule-a.git
```

```sh
$ git submodule add https://github.com/jagarsoft/submodule-b.git App/Module/submodule-b
Cloning into 'C:/Users/Usuario/GitHub/jagarsoft/submodule-a/App/Module/submodule-b'...
```

```sh
$ cat .gitmodules
[submodule "App/Module/submodule-b"]
        path = App/Module/submodule-b
        url = https://github.com/jagarsoft/submodule-b.git
```

```sh
$ git diff --cached App/Module/submodule-b
diff --git a/App/Module/submodule-b b/App/Module/submodule-b
new file mode 160000
index 0000000..b1c244e
--- /dev/null
+++ b/App/Module/submodule-b
@@ -0,0 +1 @@
+Subproject commit b1c244eeb74603d54ef113dfe25334ca92f1f34a
```

```sh
$ git diff --cached --submodule
diff --git a/.gitmodules b/.gitmodules
new file mode 100644
index 0000000..03da874
--- /dev/null
+++ b/.gitmodules
@@ -0,0 +1,3 @@
+[submodule "App/Module/submodule-b"]
+       path = App/Module/submodule-b
+       url = https://github.com/jagarsoft/submodule-b.git
Submodule App/Module/submodule-b 0000000...b1c244e (new submodule)
```


```sh
$ composer init


  Welcome to the Composer config generator



This command will guide you through creating your composer.json config.

Package name (<vendor>/<name>) [usuario/submodule-a]: jagarsoft/submodule-a
Description []: An use case of submodules in Git
Author [, n to skip]: Javier Garrido <jagarsoft2000@gmail.com>
Author [, n to skip]: n
Minimum Stability []: dev
Package Type (e.g. library, project, metapackage, composer-plugin) []: project
License []: GPL-2.0-only

Define your dependencies.

Would you like to define your dependencies (require) interactively [yes]? no
Would you like to define your dev dependencies (require-dev) interactively [yes]? no

{
    "name": "jagarsoft/submodule-a",
    "description": "An use case of submodules in Git",
    "type": "project",
    "license": "GPL-2.0-only",
    "minimum-stability": "dev",
    "require": {}
}

Do you confirm generation [yes]?
Would you like the vendor directory added to your .gitignore [yes]? yes
```

```sh
$ composer require phpunit/phpunit --dev
```

```sh
$ vendor/bin/phpunit --generate-configuration
PHPUnit 9.5.20-37-g3a36f4d48 #StandWithUkraine

Generating phpunit.xml in C:\Users\Usuario\GitHub\jagarsoft\submodule-a

Bootstrap script (relative to path shown above; default: vendor/autoload.php): tests/bootstrap/autoload.php
Tests directory (relative to path shown above; default: tests):
Source directory (relative to path shown above; default: src):
Cache directory (relative to path shown above; default: .phpunit.cache):

Generated phpunit.xml in C:\Users\Usuario\GitHub\jagarsoft\submodule-a.
Make sure to exclude the .phpunit.cache directory from version control.

Usuario@DESKTOP-RUQJ5VU MINGW64 ~/GitHub/jagarsoft/submodule-a (main)
$ echo .phpunit.cache/ >> .gitignore

```