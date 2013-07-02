Puppet Checker
==============

Simple Puppet checker and cleaner utilities for your lovely manifests.

Why use these?
--------------
If you're lazy and want better quality control.  Also check out puppet-cleaner https://github.com/santana/puppet-cleaner

Requirements
------------

  * RHEL6 (Only tested on this platform)
  * puppet
  * manifests
  * puppet-lint or WWW access for puppet-linter API

Installation
------------

    git clone https://github.com/marshyski/puppet-checker.git
    chmod 0755 ./puppet-checker/*
    mv ./puppet-checker/* /usr/bin/

Usage
-----

### puppet-checker
`puppet-checker` or `puppet-checker /location_of/module.pp`

* **What will be ran against module:** <br>
	`puppet apply --noop site.pp` - Local dry-run / no-operation(noop) on site.pp <br>
	`puppet apply --noop init.pp` - Local dry-run / no-operation(noop) of manifest <br>
	`puppet-lint init.pp` - Check Puppet manifest conforms to the style guide <br>
	`find init.pp -type f -perm /0137 -printf "%p is %m should be 0640 or less\n"` - Check if permissions are set correctly <br>
	`find $1 -type f \( ! -group $GRP \) -printf "%p is group %g should be puppet\n"` - Check if puppet group is set for readage <br>

### puppet-clean
`puppet-clean` or `puppet-clean /location_of/module.pp`

* **What will be ran against module:** <br>
	`chmod 0755 manifest_directories` - Ensure puppet can peer into directories <br>
	`chgrp puppet manifest_directories` - Ensure puppet can read the directories <br>
	`sed -i 's/[ \t]*$//' $1 init.pp` - Remove trailing white spaces <br>
	`chmod 0640 init.pp` - Remove access from other/world <br>
	`chgrp puppet init.pp` - Ensure puppet group can read modules <br>

Help & Feedback
---------------

You can email (marshyski@gmail.com) me directly if you need help, submit an issue or pull request.
