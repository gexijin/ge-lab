---
layout: post
title: "Too Many Files in a Folder in Linux"
date: 2023-04-17 19:19:22 +0000
---

**Q:** Under Linux, I am trying to use gzip to compress all 14,000 files in a folder, but I get this error: `Argument list too long`.

**GPT-4:**

> The "Argument list too long" error occurs when the number of arguments passed to a command exceeds the system's limit. To work around it, you can use the `find` command with either `-exec` or `xargs`. Here are two ways to compress all the files in a folder.
>
> **Method 1: `find` with `-exec`**
>
> ```bash
> find /path/to/folder -type f -exec gzip "{}" \;
> ```
>
> This finds all the files in the specified folder and runs `gzip` on each file individually.
>
> **Method 2: `find` with `xargs`**
>
> ```bash
> find /path/to/folder -type f -print0 | xargs -0 gzip
> ```
>
> This finds all the files in the specified folder, and `xargs` passes them to `gzip` in batches. The `-print0` option in `find` and the `-0` option in `xargs` ensure that file names with spaces or special characters are handled properly.
>
> Both methods compress each file individually, creating a separate `.gz` file for each original file. If you want a single compressed archive containing all the files, use `tar` with gzip:
>
> ```bash
> tar -czvf archive_name.tar.gz -C /path/to/folder .
> ```
>
> This creates a compressed archive (`archive_name.tar.gz`) containing all the files in the specified folder. The `-C` option changes to that folder before adding the files (represented by `.`) to the archive.

Method 1 worked perfectly.
