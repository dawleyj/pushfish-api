PushFish API Description [![License](http://img.shields.io/badge/license-BSD-blue.svg?style=flat)](/LICENSE)
==================
# Table of contents
* [motivation](https://github.com/dawleyj/pushfish-api/edit/master/README.md#motivation)
* [configuration](https://github.com/dawleyj/pushfish-api/edit/master/README.md#configuration)
* [docker](https://github.com/dawleyj/pushfish-api/edit/master/README.md#docker)
* [contributing](https://github.com/dawleyj/pushfish-api/edit/master/README.md#contributing)
* [contact](https://github.com/dawleyj/pushfish-api/edit/master/README.md#contact)

This is the core for PushFish. PushFish is an open-source alternative to Pushbullet [(pushbullet.com)](https://www.pushbullet.com/). PushFish is powered entirely by Python. In effect, pushfish allows users to integrate their push notifications across platforms like Pushbullet. Specifically, Pushfish allows notification integration across:
* Windows
* Linux
* Android

## Motivation
PushFish was created as an open-source alternative to PushBullet, allowing users to have a similar experience to PushBullet with more modularity. As an open-source app, users can share their own configurations for PushFish to make notificaiton management easier. Additionally, users can suggest and contribute features that may better the app. For example, PushBullet has options for file sharing across devices, so similar features may be added to PushFish in the future.

## Configuration
The pushfish API server reads various options from a configuration file. This configuration file can be specified by setting the environment variable `PUSHFISH_CONFIG`. If this variable is not set, then the file is searched for in a default path.

```
     ~/.config/pushfish-api/pushfish-api.cfg # on Linux 
     %APPDATA%\pushfish-api\pushfish-api.cfg # on Windows
     ~/Library/Application Support/pushfish-api/pushfish-api.cfg # on OSX
```

where the value for "user" will be changed to your current username. If this file does not exist, then the API server will generate a default configuration, which looks like this:

```
[database]
#for mysql, use something like:
#uri = 'mysql+pymysql://pushfish@localhost/pushfish_api?charset=utf8mb4'

#for sqlite (the default), use something like:
uri = sqlite:////home/pushfish/.local/share/pushfish-api/pushfish-api.db

[dispatch]
google_api_key = 
google_gcm_sender_id = 509878466986
#point this at the pushfish-connectors zeroMQ pubsub socket
zeromq_relay_uri = 

[server]
#set to 0 for production mode
debug = 1

```

the format of the database URI is an SQLAlchemy URL as [described here](http://docs.sqlalchemy.org/en/latest/core/engines.html)

Docker
------------------
The docker file is a text file that users can use to build an image. Below is a step-by-step list of instructions for building the image.
1. Build the image:

```
docker build -t pushfish-api:latest .
```

2. Run:

```
docker run pushfish-api:latest 
```

3. Run tests.py:

```
docker run pushfish-api:latest python tests.py
```
### Contributing
Stay up-to-date with contributions: [PushFish issues](https://github.com/dawleyj/pushfish-api/commits/master). Submit pull requests to the repo with your own contributions to help better PushFish! Also report bugs to our site [push.fish](push.fish).
### Contact
The creator of PushFish should include some kind of contact information here. For example:
* contact via e-mail at john@push.fish
* visit the website at [push.fish](push.fish)
