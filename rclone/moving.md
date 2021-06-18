# Server Side Move (Copy)

Moving (or renaming) objects within an S3 bucket isn't generally supported. It
is possible however with [Wasabi](https://www.wasabi.com) and
[rclone](https://rclone.org/).

Wasabi does have the ability to directly rename objects although this isn't
directly support by rclone as of March 2021.

- [Renaming Objects](https://wasabi.com/wp-content/themes/wasabi/docs/API_Guide/index.html#t=topics%2FRenaming_Objects.htm%23XREF_12310_Renaming_Objects)

However, Wasabi does have optimizations to avoid an entire (re)copy and delete
which works nicely with rclone. For large files it may take a few minutes for
this server side copy to complete depending on the file size.

Here's an example rclone command to move a file from one location to another.

````
rclone moveto backend:bucket/path1/path2/file backend:bucket/path3/path4/file
````

During the transfer you will see a very high transfer rate since nothing is
really being transferred.

````
Transferred:   	    6.554G / 6.554 GBytes, 100%, 55.987 MBytes/s, ETA 0s
````

When this is complete the following will be logged.

````
2021/02/27 17:59:45 INFO  : file: Copied (server side copy)
2021/02/27 17:59:45 INFO  : file: Deletedbackend:bucket/path1/file

````

Take care when using rclone _moveto_ and _move_. I've made some mistakes using
move:

````
rclone move backend:bucket/path1/file backend:bucket/path2/file
````

And ended up with the destination file being a directory and file:

````
backend:bucket/path2/file/file
````

This is not want I wanted and to resolve you have to use a temp file:

````
rclone moveto backend:bucket/path2/file/file backend:bucket/path2/foo
rclone moveto backend:bucket/path2/foo backend:bucket/path2/file
````
