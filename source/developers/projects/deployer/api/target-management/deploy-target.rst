.. include:: /includes/unicode-checkmark.rst

.. _crafter-deployer-api-target-deploy:

=============
Deploy Target
=============

Deploy a Crafter Deployer target.

--------------------
Resource Information
--------------------

+----------------------------+-------------------------------------------------------------------+
|| HTTP Verb                 || POST                                                             |
+----------------------------+-------------------------------------------------------------------+
|| URL                       || ``/api/1/target/deploy/:target_id``                              |
+----------------------------+-------------------------------------------------------------------+
|| Response Formats          || ``JSON``                                                         |
+----------------------------+-------------------------------------------------------------------+

----------
Parameters
----------

+-------------------------+-------------+---------------+----------------------------------------+
|| Name                   || Type       || Required     || Description                           |
+=========================+=============+===============+========================================+
|| target_id              || String     || |checkmark|  || The target ID                         |
+-------------------------+-------------+---------------+----------------------------------------+

-------
Example
-------

^^^^^^^
Request
^^^^^^^

``POST .../api/1/target/deploy/mysite``

^^^^^^^^
Response
^^^^^^^^

``Status 200 OK``

.. code-block:: json

	{
	  "target": {
	    "id": "mysite",
	    "load_date": "2017-01-31T17:08:48.308-05:00"
	  },
	  "start": "2017-01-31T17:08:50.953-05:00",
	  "end": "2017-01-31T17:08:53.279-05:00",
	  "status": "SUCCESS",
	  "change_set": {
	    "created_files": [
	      "site/website/index.xml"
	    ],
	    "updated_files": [],
	    "deleted_files": []
	  },
	  "processor_executions": [
	    {
	      "processor_name": "gitPullProcessor",
	      "start": "2017-01-31T17:08:50.96-05:00",
	      "end": "2017-01-31T17:08:51.883-05:00",
	      "status": "SUCCESS",
	      "status_details": "Successfully cloned Git remote repository /opt/crafter/repos/mysite into /opt/crafter/deployed-sites/mysite",
	      "running": false
	    },
	    {
	      "processor_name": "searchIndexingProcessor",
	      "start": "2017-01-31T17:08:51.883-05:00",
	      "end": "2017-01-31T17:08:53.279-05:00",
	      "status": "SUCCESS",
	      "status_details": {
	        "successfulUpdates": [
	          "site/website/index.xml"
	        ],
	        "successfulDeletes": [],
	        "failedUpdates": [],
	        "failedDeletes": [],
	        "attemptedUpdatesAndDeletes": 1
	      },
	      "running": false
	    }
	  ],
	  "running": false
	}

---------
Responses
---------

+---------+----------------------------------+---------------------------------------------------+
|| Status || Location                        || Response Body                                    |
+=========+==================================+===================================================+
|| 200    ||                                 || See example above                                |
+---------+----------------------------------+---------------------------------------------------+
|| 404    ||                                 || ``{ "message" : "Target not found" }``           |
+---------+----------------------------------+---------------------------------------------------+
|| 500    ||                                 || ``{ "message" : "Internal server error" }``      |
+---------+----------------------------------+---------------------------------------------------+
