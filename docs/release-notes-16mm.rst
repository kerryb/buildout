=============================================
GroupServer 16.mm — Pastis proffered politely
=============================================

:Authors: `Michael JasonSmith`_;
:Contact: Michael JasonSmith <mpj17@onlinegroups.net>
:Date: 2016-01-26
:Organization: `GroupServer.org`_
:Copyright: This document is licensed under a
  `Creative Commons Attribution-Share Alike 4.0 International
  License`_ by `OnlineGroups.net`_.

..  _Creative Commons Attribution-Share Alike 4.0 International License:
    https://creativecommons.org/licenses/by-sa/4.0/

.. highlight:: console

------------
Introduction
------------

Of the visible `changes to GroupServer`_ in the Pastis release
the most significant is the new Change email settings page. You
can `get Pastis`_ immediately.

----------------------
Changes to GroupServer
----------------------

The `Email-settings page`_ is now easier to use with mobile
phones. The other major update in this release is the `updated
base packages`_. Finally, there have been some `minor
improvements`_.

.. index::
   single: Profile
   pair: Email; Settings
   pair: JavaScript; jQuery.UI
   pair: JavaScript; Bootstrap

Email-settings page
===================

The Change email settings page allows people to add email addresses, and
set the addresses they prefer. The page has been updated so it is
**easier to use** with mobile devices, with buttons allowing
people to add and remove addresses from each list of
addresses. Using drag-and-drop between the lists still works for
those on desktop systems.

The underlying code now uses web-hooks and JSON to update the
email settings. This results in a far-faster page than before.

Finally, the dependencies that the Change email settings page had
on ``jQuery.UI`` and Twitter Bootstrap have been removed.

.. index::
   single: Dependencies
   pair: Install; Buildout
   pair: JavaScript; jQuery
   pair: JavaScript; MultiFile
   pair: JavaScript; WYMeditor

Updated base packages
=====================

The most visible dependency to change in Pastis is jQuery_, which
has been updated to version 1.12.0, from 1.9.1. This should be
compatible with any customisation code that exists for
GroupServer, as the API for jQuery remains the same. Following
the change to jQuery

* The WYMeditor_ has been updated to 1.1.1 from 1.0.0b5, and
* The `jQuery MultiFile`_ plugin has been updated to 2.2.1 from
  1.48.

The Zope2_ application framework, which supports GroupServer, has
been updated to version 2.13.23 from 2.13.22. The buildout_
system, which controls most of the installation and update
process, has been updated to use `zc.buildout 2.3.1`_.

In addition packages such as dnspython_, enum34_, lxml_,
premailer_, pytz_, Pillow_, requests_, and six_ have also been
updated.

.. _buildout: http://www.buildout.org/en/latest/
.. _dnspython: https://pypi.python.org/pypi/dnspython
.. _enum34: https://pypi.python.org/pypi/six
.. _jQuery: http://jquery.com/
.. _jQuery MultiFile: http://www.fyneworks.com/jquery/multifile/
.. _lxml: https://pypi.python.org/pypi/lxml
.. _premailer: https://pypi.python.org/pypi/premailer
.. _pytz: https://pypi.python.org/pypi/pytz
.. _Pillow: https://pypi.python.org/pypi/Pillow
.. _requests: https://pypi.python.org/pypi/requests
.. _six: https://pypi.python.org/pypi/six
.. _WYMeditor: http://wymeditor.github.io/wymeditor/
.. _zc.buildout 2.3.1: https://pypi.python.org/pypi/zc.buildout/2.3.1
.. _Zope2: https://pypi.python.org/pypi/Zope2

.. index::
   single: Administration
   single: Installation
   single: Unit tests
   single: Continuous integration
   pair: Email; Can post
   pair: Internationalisation; German
   pair: JavaScript; Style guide
   pair: Notification: Confirm subscription
   triple: Group; Type; Announcement

Minor improvements
==================

* The **Admin** section of the group page has been moved up, so
  it stays in once place while the dynamic *Members* and *Recent
  files* sections load.

* The **Manage members** page has been updated, so it is easier
  to use, it looks better, and includes internationalisation
  support. A coding error that prevented a group administrator
  from being a posting member of an *announcement* group has been
  corrected.

* The **German translation** has been updated, thanks to Alice
  and `Stephan G. Blendinger`_.

* The :mailheader:`From` address used in the *Confirm
  subscription* notification has been fixed, so it is now set to
  the email-address of the group rather than the support email
  address. Thanks to `Jp Maxwell`_ for spotting the issue.

* The code that provides the **image scaling** now handles some
  errors in a more robust way.

* The **installation script** :program:`gs_install_ubuntu.sh` now
  uses bold and muted text to make the information hierarchy more
  clear.

* The JavaScript code that makes up GroupServer has been updated
  to conform to the `Google JavaScript Style Guide`_, thanks to
  the use of the `Google Closure Linter`_.

* The code that determines if someone **can post** has been
  updated so it is more thoroughly tested.

* More **unit tests** have been added to the products that make
  up GroupServer.

* All the unit-tests now can be run by the script generated by
  `zc.recipe.testrunner`_::

    $ ./bin/testrunner -v -c -m "gs\..*"

  This script is run by the new **continuous integration** system
  provided by `Travis CI`_.

* More JavaScript has been switched to use *strict mode.* This
  includes the code that supports **Registration.**

.. _Stephan G. Blendinger:
   https://www.transifex.com/user/profile/stephanblendinger/

.. _Jp Maxwell: http://groupserver.org/p/4JbY4KDDFPrgfnMmgkZ31v

.. _Google JavaScript Style Guide:
   https://google.github.io/styleguide/javascriptguide.xml

.. _Google Closure Linter:
   https://developers.google.com/closure/utilities/

.. _zc.recipe.testrunner:
   https://pypi.python.org/pypi/zc.recipe.testrunner/

.. _Travis CI: https://travis-ci.org/groupserver/

----------
Get Pastis
----------

To get Pastis go to `the Downloads page for GroupServer`_
and follow `the GroupServer Installation documentation`_. Those
who already have a functioning installation can `update an
existing GroupServer system`_.

..  _The Downloads page for GroupServer: http://groupserver.org/downloads
..  _The GroupServer Installation documentation:
    http://groupserver.readthedocs.org/

Update an Existing GroupServer System
=====================================

To update a system running the Limoncello (15.11) release of
GroupServer to Pastis (16.mm) carry out the following steps.

#.  Copy the new versions of the configuration files to your
    existing GroupServer installation:

      ::

        $ cp ../groupserver-16.mm/[bivz]*cfg  .

#.  Run ``buildout`` in your existing GroupServer installation:

      ::

        $ ./bin/buildout -N

#.  Restart your GroupServer instance (see
    :doc:`groupserver-start`).

---------
Resources
---------

- Code repository: https://github.com/groupserver/
- Questions and comments to
  http://groupserver.org/groups/development
- Report bugs at https://redmine.iopen.net/projects/groupserver

..  _GroupServer: http://groupserver.org/
..  _GroupServer.org: http://groupserver.org/
..  _OnlineGroups.Net: https://onlinegroups.net/
..  _Michael JasonSmith: http://groupserver.org/p/mpj17
..  _Dan Randow: http://groupserver.org/p/danr
..  _Bill Bushey: http://groupserver.org/p/wbushey
..  _Alice Rose: https://twitter.com/heldinz
..  _E-Democracy.org: http://forums.e-democracy.org/

..  LocalWords:  refactored iopen JPEG redmine jQuery jquery async Rakı Bushey
..  LocalWords:  Randow Organization sectnum Slivovica DMARC CSS Calvados AIRA
..  LocalWords:  SMTP smtp mbox CSV Transifex cfg mkdir groupserver Vimeo WAI
..  LocalWords:  buildout Limoncello iframe Pastis Linter
