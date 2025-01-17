=========
Changelog
=========

19.4.0 / 2015/11/20
===================

Core
++++

- fix: make sure that a user is able to access to the logs after dropping a
  privilege (:issue:`1116`)
- improvement: inherit the `Exception` class where it needs to be (:issue:`997`)
- fix: make sure headers are always encodedas latin1 RFC 2616 (:issue:`1102`)
- improvement: reduce arbiter noise (:issue:`1078`)
- fix: don't close the unix socket when the worker exit (:issue:`1088`)
- improvement: Make last logged worker count an explicit instance var (:issue:`1078`)
- improvement: prefix config file with its type (:issue:`836`)
- improvement: pidfile handing (:issue:`1042`)
- fix: catch OSError as well as ValueError on race condition (:issue:`1052`)
- improve support of ipv6 by backporting urlparse.urlsplit from Python 2.7 to
  Python 2.6.
- fix: raise InvalidRequestLine when the line contains maliscious data
  (:issue:`1023`)
- fix: fix argument to disable sendfile
- fix: add gthread to the list of supported workers (:issue:`1011`)
- improvement: retry socket binding up to five times upon EADDRNOTAVAIL
  (:issue:`1004`)
- **breaking change**: only honor headers that can be encoded in ascii to comply to
  the RFC 7230 (See :issue:`1151`).

Logging
+++++++

- add new parameters to access log (:issue:`1132`)
- fix: make sure that files handles are correctly reopenebd on HUP
  (:issue:`627`)
- include request URL in error message (:issue:`1071`)
- get username in access logs (:issue:`1069`)
- fix statsd logging support on Python 3 (:issue:`1010`)

Testing
+++++++

- use last version of mock.
- many fixes in Travis CI support
- miscellaneous improvements in tests

Thread worker
+++++++++++++

- fix: Fix self.nr usage in ThreadedWorker so that auto restart works as
  expected (:issue:`1031`)

Gevent worker
+++++++++++++

- fix quit signal handling (:issue:`1128`)
- add support for Python 3 (:issue:`1066`)
- fix: make graceful shutdown thread-safe (:issue:`1032`)

Tornado worker
++++++++++++++

- fix ssl options (:issue:`1146`, :issue:`1135`)
- don't check timeout when stopping gracefully (:issue:`1106`)

AIOHttp worker
++++++++++++++

- add SSL support (:issue:`1105`)

Documentation
+++++++++++++

- fix link to proc name setting (:issue:`1144`)
- fix worker class documentation (:issue:`1141`, :issue:`1104`)
- clarify graceful timeout documentation (:issue:`1137`)
- don't duplicate NGINX config files examples (:issue:`1050`, :issue:`1048`)
- add `web.py` framework example (:issue:`1117`)
- update Debian/Ubuntu installations instructions (:issue:`1112`)
- clarify `pythonpath` setting description (:issue:`1080`)
- tweak some example for python3
- clarify `sendfile` documentation
- miscellaneous typos in source code comments (thanks!)
- clarify why REMOTE_ADD may not be the user's IP address (:issue:`1037`)


Misc
++++

- fix: reloader should survive SyntaxError (:issue:`994`)
- fix: expose the reloader class to the worker.


19.3.0 / 2015/03/06
===================

Changes
-------

Core
++++

- fix: :issue:`978` make sure a listener is inheritable
- add `check_config` class method to workers
- fix: :issue:`983` fix select timeout in sync worker with multiple
  connections
- allows workers to access to the reloader. close :issue:`984`
- raise TypeError instead of AssertionError

Logging
+++++++

- make Logger.loglevel a class attribute

Documentation
+++++++++++++

- fix: :issue:`988` fix syntax errors in examples/gunicorn_rc

19.2.1 / 2015/02/4
==================

Changes
-------

Logging
+++++++

- expose loglevel in the Logger class

AsyncIO worker (gaiohttp)
+++++++++++++++++++++++++

- fix :issue:`977` fix initial crash

Documentation
+++++++++++++

- document security mailing-list in the contributing page.


19.2 / 2015/01/30
=================

Changes
-------

Core
++++

- optimize the sync workers when listening on a single interface
- add `--sendfile` settings to enable/disable sendfile. fix :issue:`856` .
- add the selectors module to the code base. :issue:`886`
- fix :pr:`862` add `--max-requests-jitter` setting to set the maximum jitter to add to the
  max-requests setting.
- fix :issue:`899` propagate proxy_protocol_info to keep-alive requests
- fix :issue:`863` worker timeout: dynamic timeout has been removed, fix a race
  condition error
- fix: Avoid world writable file
- fix :issue:`917`: the deprecated ``--debug`` option has been removed.

Logging
+++++++

- fix :issue:`941`  set logconfig default to paster more trivially
- add statsd-prefix config setting: set the prefix to use when emitting statsd
  metrics
- :issue:`832` log to console by default
- fix :issue:`845`: set the gunicorn loggers from the paste config

Thread Worker
+++++++++++++

- fix :issue:`908` make sure the worker can continue to accept requests

Eventlet Worker
+++++++++++++++

- fix :issue:`867` Fix eventlet shutdown to actively shut down the workers.

Documentation
+++++++++++++

Many improvements and fixes have been done, see the detailed changelog for
more information.

History
=======

.. toctree::
   :titlesonly:

   2015-news
   2014-news
   2013-news
   2012-news
   2011-news
   2010-news
