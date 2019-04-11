

==================================
Installation
==================================

----------------------------------
Virtual environment
----------------------------------
**Hint**
On Windows use ``python`` instead of ``python3``

#. Navigate to the folder where the virtual environment shall be created (e.g.)::

    cd /opt

#. Create virtual environment (this will create a new folder "habapp")::

    python3 -m venv habapp

#. Go into folder of virtual environment::

    cd habapp

#. Activate the virtual environment

   Linux::

    source bin/activate

   Windows::

    Scripts\activate

#. Upgrade pip::

    python3 -m pip install --upgrade pip

#. Install HABApp::

    python3 -m pip install habapp

#. Run HABApp::

    habapp --config PATH_TO_CONFIGURATION_FOLDER


----------------------------------
Autostart on Linux
----------------------------------
To automatically start HABApp from the virtual environment after a reboot call::

    nano /etc/systemd/system/habapp.service


and copy paste the following contents. If the user which is running openhab is not "openhab" replace accordingly::

    [Unit]
    Description=HABApp
    After=network-online.target
    
    [Service]
    Type=simple
    User=openhab
    Group=openhab
    ExecStart=/opt/habapp/bin/habapp -c PATH_TO_CONFIGURATION_FOLDER
    
    [Install]
    WantedBy=multi-user.target

Press Ctrl + x to save.

Now execute the following commands to enable autostart::

    sudo systemctl --system daemon-reload
    sudo systemctl enable habapp.service

It is now possible to start and check the status of HABApp with::

    sudo systemctl start habapp.service
    sudo systemctl status habapp.service

----------------------------------
Docker
----------------------------------
Installation through `Link docker <https://hub.docker.com/r/spacemanspiff2007/habapp>`_ is also available::

    docker pull spacemanspiff2007/habapp