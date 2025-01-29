# rockon-registry

This repository consists of Rock-on (Docker based apps) configuration profiles
formatted as JSON files. The Rock-on framework of Rockstor parses a well
formatted profile and provides a generic management and workflow such as
install, uninstall, update, start and stop.

## Can You Show Me an Example??

Look at any <name>.json file in this repository. A simpler example is
[syncthing.json](https://github.com/rockstor/rockon-registry/blob/master/syncthing.json). The structure is fairly intuitive though cumbersome. Using existing examples and the description below of the `json` structure should make it clearer on how this framework is organized.

## How Can I Add My Own Rock-on?

If you are familiar with Docker and know how to deploy docker containers using the command line, you can create a Rock-on for the same with little effort.
You can find instructions in the [Rockstor Documentation](https://rockstor.com/docs/contribute/contribute_rockons.html) both for running your own Rock-on locally, as well as how to contribute to the existing public repository of available Rock-ons

## What Is the Structure of a Rock-on Profile File?

It is a big mass of JSON with nested objects, arrays and values.

### Top Level Structure
```
{
    "<Rock-on name. eg: LSIO-Plex>": {
      "description": "<description of the Rock-on. Eg: Plex brought to you by Linuxserver.io>",
      "version": "<arbitrary version string>",
      "website": "<Underlying app website>",
      (optional)"icon": "<link to icon, if any>",
      (optional)"more_info": "<string or html with more information to display to the user in the Rockstor UI>",
      (optional)"ui":{
                "slug":"gui", link to webui becomes ROCKSTOR_IP:PORT/gui with slug value gui
      },
      (optional)"volume_add_support": true, If the app allows arbitrary Shares to be mapped to the main container>,
      "containers": {
        "<container1 name>": <container object representing the main container. see below>,
        "<container2 name>": <container object representing the second container, if any. see below>, ...
      },
      (optional)"custom_config": <custom configuration object that a special install handler of this Rock-on expects>
    }
}
```
