## Info:
- change payment form
- lock login to admin panel
- change file content without modify time (https://ostechnix.com/how-to-edit-a-file-without-changing-its-timestamps-in-linux/)
- add file with random_name.jpg in ./img/ catalog
- install by posting on ./b2b.php

## To fix you need:
- replace /classes and /controllers folder with the one from backup
- delete random_name.jpg from ./img/ catalog
- delete ./b2b.php if exists
- delete cache/class_index.php
- clear ./var/cache
- and add at the bottom of the flies:

`/public_html/img/.htaccess`

    # Prevent execution of php scripts from img folder
    <FilesMatch "\.(?i:php)$">
        # Apache 2.2
        <IfModule !mod_authz_core.c>
            Order allow,deny
            Deny from all
        </IfModule>

        # Apache 2.4
        <IfModule mod_authz_core.c>
            Require all denied
        </IfModule>
    </FilesMatch>
    
`/public_html/.htaccess`

    # Prevent execution of b2b.php (wirus)
    <Files "b2b.php">
        # Apache 2.2
        <IfModule !mod_authz_core.c>
            Order deny,allow
            Deny from all
        </IfModule>

        # Apache 2.4
        <IfModule mod_authz_core.c>
            Require all denied
        </IfModule>
    </Files>
