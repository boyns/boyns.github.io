My github hosted version of [KeeWeb](https://keeweb.info/). Follow the link
below to access this version of KeeWeb:

[https://boyns.github.io/keeweb/](https://boyns.github.io/keeweb/)

KeeWeb releases can be found here:

[Releases](https://github.com/keeweb/keeweb/releases)

Steps to add a new release:

1. Download release zip

````
$ wget https://github.com/keeweb/keeweb/releases/download/v1.16.7/KeeWeb-1.16.7.html.zip
````

2. Remove old release

```
$ cd keeweb
$ find . -type f | xargs git rm
```

3. Unpack the new release within keeweb directory

````
$ unzip ~/Downloads/KeeWeb-1.16.7.html.zip
````

4. Commit and push

````
$ git add .
$ git commit -a
$ git push origin
````
