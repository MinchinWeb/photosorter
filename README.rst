photosorter
===========

.. image:: https://img.shields.io/pypi/v/colourettu.svg?style=flat
    :target: https://pypi.python.org/pypi/colourettu/

.. image:: https://travis-ci.org/MinchinWeb/minchin.scripts.photosorter.svg?branch=master
    :target: https://travis-ci.org/dbader/photosorter)
.. image:: https://coveralls.io/repos/MinchinWeb/minchin.scripts.photosorter/badge.svg?branch=master
    :target: https://coveralls.io/r/dbader/photosorter?branch=master

A little Python script to keep my photos organized on Dropbox. Designed to be
run intermittently, but will run forever by default.

It watches a *source directory* for modifications and moves new image files to
a *target directory* depending on when the photo was taken, using EXIF data and
creation date as a fallback.

Directory and file names follow a simple naming convention
(`YYYY-MM/YYYY-MM-DD hh:mm:ss.ext`) that keeps everything neatly organized.
Duplicates are detected and ignored based on their SHA1 hash. Photos taken in
the same instant get de-duplicated by adding a suffix (`-1`, `-2`, etc) to
their filenames.

The result looks somewhat like this:

    ├── 2013
    │   ├── 2013-01
    │   │   ├── 2013-01-05\ 13.24.45.jpg
    │   │   ├── 2013-01-05\ 14.25.54.jpg
    │   │   ├── 2013-01-05\ 21.28.48-1.jpg
    │   │   ├── 2013-01-06\ 16.05.02.jpg
    │   │   ├── 2013-01-06\ 19.59.25.jpg
    │   │   ├── 2013-01-06\ 20.40.28.jpg
    │   │   ├── 2013-01-06\ 21.14.38.jpg
    │   │   ├── 2013-01-08\ 11.45.51.jpg
    │   ├── 2013-02
    │   |   ├─ ...
    │   ├── ...
    │   └── 2013-12
    ├── 2014
    │   ├── 2014-01
    │   ├── 2014-02
    │   ├── ...
    │   └── 2014-12
    ├── ...

I use ``C:\Users\[windows username\Dropbox\Camera Uploads`` as the source
directory and ``Z:\Photos`` as the target. This allows me to move my photo from
Dropbox to a local drive, and merge them with the rest of my photo collection.

Inspired by

- <http://simplicitybliss.com/exporting-your-iphoto-library-to-dropbox/>
- <https://github.com/wting/exifrenamer>
- <http://chambersdaily.com/learning-to-love-photo-management/>
- <https://dbader.org/blog/how-to-store-photos-in-the-cloud-and-avoid-vendor-lock-in>

Setup
-----

The easiest way to install the script is through pip:

    > pip install minchin.scripts.photosorter

Run
---

Watch `src_dir` and sort incoming photos into `dest_dir`.

    > photosorter src_dir dest_dir

When you're done with it, `Ctrl + C` will end the program.

<!--

## Run on startup

1. Move `photosorter.conf.example` to `/etc/init` as `photosorter.conf`
   and edit it to suit your needs by replacing the user, source and target
   directories.
2. Run `$ sudo start photosorter`.
3. Check the logs at `/var/log/upstart/photosorter.log`.
-->

Meta
----

Distributed under the MIT license. See ``LICENSE`` for more information.

https://github.com/MinchinWeb/minchin.scripts.photosorter