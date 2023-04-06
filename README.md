## Search last changes (30 days)

    find ./ -mtime -30 -type f -printf "%TY-%Tm-%Td %TH:%TM %p\n" | sort -r | head -n 50

    find . -mtime -30 -type f ! -path "./var/cache/*" ! -path "./var/logs/*" ! -path "./cache/*" ! -path "./img/*" -printf "%TY-%Tm-%Td %TH:%TM %p\n" | sort -r | head -n 50
    
where

`-type f` - only files

`-mtime -30` - last 30 days

`! -path "./var/cache/*" ...` - exclude ./var/cache/* directory

`head -n 50` - show only 50 files


## Diff between files - with code
    diff -bur ./classes/ ~/bkp/classes/
 
where

`b` flag means ignoring whitespace

`u` flag means a unified context (3 lines before and after)

`r` flag means recursive

## Diff between files - only filenames
    diff -qr ./classes/ ~/bkp/classes/
 
where

`q` flag means only filenames

`r` flag means recursive

