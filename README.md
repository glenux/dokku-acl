# dokku-acl (beta) [![Build Status](https://img.shields.io/travis/dokku/dokku-acl.svg?branch=master "Build Status")](https://travis-ci.org/dokku/dokku-acl) [![IRC Network](https://img.shields.io/badge/irc-freenode-blue.svg "IRC Freenode")](https://webchat.freenode.net/?channels=dokku)

Unofficial ACL plugin for dokku.

:warning: __CODE IS STILL UNSTABLE. DO NOT USE__

## Requirements

- dokku 0.4.x+
- docker 1.8.x

## Installation

```shell
# on 0.4.x+
sudo dokku plugin:install https://github.com/glenux/dokku-acl.git acl
```

## Commands

:warning: NOT YET IMPLEMENTED

```
acl:list [app]               List all user permissions for app (for all apps otherwise)

acl:create <group>           Create a user group
acl:destroy <group>          Delete a user group
acl:grant <group> <app> <actions,...> 
acl:revoke <group> <app> <actions,...> 
```

## usage

```shell
# create three user groups named lolipop
dokku acl:create admin
dokku acl:create demo-admin
dokku acl:create demo-read

# join users (via ssh-keys) to these groups
dokku acl:join admin glenn_rsa

dokku acl:join demo-admin roland_rsa
dokku acl:join demo-deploy jerome_rsa
dokku acl:join demo-deploy sebastian_rsa

# remove user from a group
dokku acl:leave demo-deploy sebastian_rsa

# give all permissions to admin on all apps
dokku acl:grant admin ALL ALL

# give all permissions to demo-admin on demo apps
dokku acl:grant demo-admin demo ALL

# give git push/pull permissions to demo-deploy on demo apps
dokku acl:grant demo-deploy demo git-receive-pack,git-upload-pack

# remove all permissions to deploy-deploy on demo apps
dokku acl:revoke demo-deploy demo ALL 
```

