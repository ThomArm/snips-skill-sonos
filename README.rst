Sonos skill for Snips
=====================

|Build Status| |PyPI| |MIT License|

A Snips Skill to control one Sonos speaker on your local network.

Snips Manager
-------------

Installation
^^^^^^^^^^^^

It is recommended that you use this skill with the `Snips Manager
<https://github.com/snipsco/snipsskills>`_. Simply add the following section to
your `Snipsfile <https://github.com/snipsco/snipsskills/wiki/The-Snipsfile>`_:

.. code-block:: yaml

    skills:
      - package_name: snipssonos
        class_name: SnipsSonos
        pip: https://github.com/snipsco/snips-skills-sonos

Usage with Sonos Local Music Library
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you would like to use your local music (e.g. on a NAS, iTunes library, ...).
Follow the instruction `here
<https://sonos.custhelp.com/app/answers/detail/a_id/261/~/adding-and-updating-your-music-library>`_
.

| To create a NAS within your Raspberry Pi by following
  `this guide <https://eltechs.com/raspberry-pi-nas-guide/>`_.

| To create a local playlist follow
  `this Gist <https://gist.github.com/scarlson/944860>`_.

Usage with music service
^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: yaml

    skills:
      - package_name: snipssonos
        class_name: SnipsSonos
        pip: https://github.com/snipsco/snips-skills-sonos
        params:
          - music_service:
              - spotify
              - apple

To use music services

.. code-block:: console

    cd /home/pi
    git clone https://github.com/jishi/node-sonos-http-api

Follow this `instructions
<https://github.com/jishi/node-sonos-http-api/blob/master/README.md>`_ to
add any music sevice

Usage with Spotify with Soco library
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: yaml

    skills:
      - package_name: snipssonos
        class_name: SnipsSonos
        pip: https://github.com/snipsco/snips-skills-sonos
        params:
            spotify_refresh_token: SPOTIFY_REFRESH_TOKEN

The ``SPOTIFY_REFRESH_TOKEN`` is used for playing music from Spotify. You can
obtain it from the
`Snips Spotify Login <https://snips-spotify-login.herokuapp.com>`_ page.

There is an known issue with the library used to connect to Spotify.
To play a Spotify playlist, please import your Spotify playlists to your Sonos
playlist.

All optional parameters
^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: yaml

        params:
            spotify_refresh_token: SPOTIFY_REFRESH_TOKEN
            default_speaker: 0
            sonos_ip: XXX.XXX.XXX.XXX

spotify_refresh_token
  set spotify refresh token.

default_speaker
  The default speaker used with the skill.

sonos_ip
  If you already have the IP address of your Sonos speaker, you can set it.

Standalone
----------

Installation
^^^^^^^^^^^^

The skill is on `PyPI <https://pypi.python.org/pypi/snipssonos>`_, so you can just
install it with `pip <http://www.pip-installer.org>`_:

.. code-block:: console

    $ pip install snipssonos

Usage
^^^^^

The skill allows you to control
`Sonos <http://musicpartners.sonos.com/docs?q=node/442>`_ speakers. You can use
it as follows:

.. code-block:: python

    from snipssonos.snipssonos import SnipsSonos

    sonos = SnipsSonos(SPOTIFY_REFRESH_TOKEN)
    sonos.play_artist("John Coltrane")

Copyright
---------

This skill is provided by `Snips <https://www.snips.ai>`_ as Open Source
software. See `LICENSE.txt
<https://github.com/snipsco/snips-skill-hue/blob/master/LICENSE.txt>`_ for more
information.

.. |Build Status| image:: https://travis-ci.org/snipsco/snips-skill-sonos.svg
   :target: https://travis-ci.org/snipsco/snips-skill-sonos
   :alt: Build Status
.. |PyPI| image:: https://img.shields.io/pypi/v/snipssonos.svg
   :target: https://pypi.python.org/pypi/snipssonos
   :alt: PyPI
.. |MIT License| image:: https://img.shields.io/badge/license-MIT-blue.svg
   :target: https://raw.githubusercontent.com/snipsco/snips-skill-hue/master/LICENSE.txt
   :alt: MIT License
