tucan
-----

Notifies you via email when there are new grades available in
the campus management system of Technische Universität Darmstadt.

Installation
````````````

It might be better to use your system's package manager to install
the required dependencies:

.. code:: bash

    apt-get install python-mechanize python-lxml


Setup
`````

Set your username and password:

.. code:: bash

    cat << EOF >> ~/.netrc
    machine www.tucan.tu-darmstadt.de
        login ab34abab
        password secret
    EOF

Manual checking
```````````````

Run

.. code:: bash

    python tucan.py

to print all grades in the current semester:

.. code:: bash

    python tucan.py -n

to print only new grades.

Periodic checking
`````````````````

Edit your crontab

.. code:: bash

    crontab -e

And add this in order to check every 60 minutes:

.. code:: bash

    */60 * * * * /usr/bin/python PATH_TO_REPO_FOLDER/tucan.py -m me@email.com

Help
````

.. code:: text

    usage: python tucan.py [-h] [--mail MAIL] [--db DB] [--new] [--json]

    TUCaN script

    optional arguments:
      -h, --help            show this help message and exit
      --mail MAIL, -m MAIL  send email to this address on changes (default: None)
      --db DB               database file (default: %HOME_DIR%/.tucandb)
      --new                 print only new grades (default: False)
      --json, -j            output json (default: False)
