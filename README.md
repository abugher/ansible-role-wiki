# Bugs

# initial deployment failure

This role is incomplete.  It will not deploy a working installation.  These steps should bootstrap the server:

1.  Deploy the role.

2.  Restore the database from a backup, if possible.  Otherwise, remove `/etc/mediawiki/LocalSettings.php` from the target, browse the wiki, and complete a setup process when prompted.    

3.  Deploy again.

# PHP timeouts

After initial installation and setup, connections failed with a blank page.  Web server logs showed a timeout waiting for PHP to finish.  I increased `max_exection_time` in `/etc/php/8.2/fpm/php.ini` from 30 to 300 and restarted `php8.2-fpm`.  After that, I saw a different timeout error.  After investigating several minutes, I noticed the wiki had started working.  I reduced `max_execution_time` to its default and restarted `php8.2-fpm` again.  The wiki seems to work, still.  I have not understood this sequence of events, so I am recording it instead.

