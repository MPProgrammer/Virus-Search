## Search last changes (30 days)

    find ./ -mtime -30 -type f -printf "%TY-%Tm-%Td %TH:%TM %p\n" | sort -r | head -n 50

or

    find . -mtime -30 -type f ! -path "./var/cache/*" ! -path "./var/logs/*" ! -path "./cache/*" ! -path "./img/*" -printf "%TY-%Tm-%Td %TH:%TM %p\n" | sort -r | head -n 50
    
where

`-type f` - only files

`-mtime -30` - modification time in 30 days

`-ctime -30` - creation time in 30 days

`! -path "./var/cache/*" ...` - exclude ./var/cache/* directory

`head -n 50` - show only 50 files

<br />
<br />

## Find files modified within the last 60 days and containing the "<?php" string
    find ./ -mtime -60 -type f -exec grep -li "<?php" {} \;

and do not have the extension ".php"

    find ./ -mtime -60 -type f -not -name "*.php" -exec grep -li "<?php" {} \;
 
where

`-mtime -60` - Files modified within the last 60 days

`-type f` - Only regular files (not directories or special files)

`-not -name "*.php"` - Exclude files with the extension ".php"

`-exec grep -li "<?php" {} \;` - Execute the grep command to search for "<?php" in each file and print the filename if found

<br />
<br />

## Diff between files - with code
    diff -bur ./classes/ ~/bkp/classes/
 
where

`b` flag means ignoring whitespace

`u` flag means a unified context (3 lines before and after)

`r` flag means recursive

<br />
<br />

## Diff between files - only filenames
    diff -qr ./classes/ ~/bkp/classes/
 
where

`q` flag means only filenames

`r` flag means recursive

<br />
<br />


## After fix

1. Check if there is a new admin and remove it
2. Change passwords for admins
3. Add htpasswd to admin directory
