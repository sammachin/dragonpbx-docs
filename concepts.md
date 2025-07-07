---
title: 'Concepts'
description: 'Start building awesome documentation in under 5 minutes'
---

# Domain
Top level container in the system, calls and devices are all managed within the contruct of a domain,
Identified by unqiue FQDN, and Domain ID

# Endpoints
Collective term for Trunks and Clients withing the context of a domain
Endpoints have dialplans associated with them

# Trunk
A SIP connection to an external system, inbound traffic is identified by IP addresses, outbound traffic is sent to a FQDN (or IP) and port
Can optionally use authentication and can make outbound SIP registrations.
Does not accept inbound registration (see clients)
Defined in config.json identified by ID
Dialplan is associated in config file

# Clients
A SIP Endpoint that registers to the system and calls a RegHook to authenticate the connection
Defined in config.json by the username field, may be a regex eg `1xxx`

# Dialplans
Configuration that is linked to an endpoint consisting of a a string/pattern and a callHook url, when an endpoint initiates a call the dialled digits are matched against that endpoints dialplan to determine where to send the call hook

# Call Hooks
An event that is emitted from the system when a new call is received from and endpoint and matched in the dialplan, usually sent as a webhook the callHook payload will contain details of the call attempt.

## Call Script
A call script is returned by the users application in response to a callHook, the Call Script is a JSON document consisting of an array of verb objects

## Verbs
These are the building blocks of call routing, each object has a verb key and then additional configuration parameters.

## Settings
The settings file controls the behaviour of the PBX with things like default values and timers

## Config
The Config file manages the endpoints that can connect to the PBX, currently the config is a json file but this may move to a database in a future version.

## Meida Files
The platform 