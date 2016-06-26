
# Compose & variables

We may use environment variables to modify docker-compose behaviour.

It's kind of an hidden feature, not well documented.
I discovered about it ending up for other reasons on this pull request:

https://github.com/docker/compose/pull/1765

## Example

```bash

# Set the variable
bash-4.3$ export JUSTATEST='itworks'

# Run containers
bash-4.3$ docker-compose up -d
Creating composeinterpolation_service_1

# Check variables
bash-4.3$ docker-compose exec service env
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
HOSTNAME=9eaa80f2bd2d
mylabel=itworks
no_proxy=*.local, 169.254/16
HOME=/root

```

Note that `mylabel` was set by using the environment variable
in the docker daemon host.

## What to be used for

A first idea could be using bash/python to read a configuration file
that sets credentials and similar for containers, used by docker-compose.

I would prefer python but in that case it should be Python2 compliant
or either run the configuration reading within a docker container.



