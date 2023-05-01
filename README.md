# interlok-installer-cmd

[![GitHub tag](https://img.shields.io/github/tag/adaptris/interlok-installer-cmd.svg)](https://github.com/adaptris/interlok-installer-cmd/tags) [![license](https://img.shields.io/github/license/adaptris/interlok-installer-cmd.svg)](https://github.com/adaptris/interlok-installer-cmd/blob/develop/LICENSE)

Command line installer for Interlok. This automatically downloads the selected optional components along with the base system to build an Interlok installation in your preferred location.

* It uses gradle behind the scenes.
* It makes use our parent build.gradle https://github.com/adaptris-labs/interlok-build-parent and work in the same way as https://github.com/adaptris-labs/interlok-install-builder.

## Build

### Zip or Tar (Jar + Script)

```
$ ./gradlew clean assemble
```

## Execute

First unzip or untar the archive file, then launch bin/interlok-installer.bat or bin/interlok-installer depending if you are on windows or linux/mac.
Use the property `interlokDistDirectory` to specify the directory where you want to install Interlok.

```
./interlok-installer -DinterlokDistDirectory=/opt/Adaptris/Interlok
```

All the base configuration is stored in gradle.properties which can be overriden on the command line.

```
./interlok-installer -DinterlokVersion=4.2.0-RELEASE -DincludeWar=false -DinterlokDistDirectory=/opt/Adaptris/Interlok
```

If you want to include a different maven compatible nexus instance (either you're mirroring our public repo, or private dependencies are stored there) then you can also do this either as a system property or do it when the installer window presents itself.

```
./interlok-installer -DadditionalNexusBaseUrl=http://your-nexus.com/path/to/content -DinterlokDistDirectory=/opt/Adaptris/Interlok
```

All the available optional components for the installer version are listed in the optional-components.list file.
You need to uncomment the optional components you wish to install with the Interlok.

e.g. If you want to install interlok-jslt and interlok-json, it should be like:

```
...
## Interlok Transform/JQ - Transform JSON using JQ style syntax ##
# com.adaptris:interlok-jq
## Interlok Transform/JSLT - Support for JSON transforms via JSLT ##
com.adaptris:interlok-jslt
## Interlok Transform/JSON - Everything JSON related; transformations, schemas, json-path (xpath-alike), splitting ##
com.adaptris:interlok-json
## Interlok Transform/JSON Streaming - Streaming JSON in a STaX-alike manner ##
# com.adaptris:interlok-json-streaming
...
```

## Notes

* To start the installed Interlok you can either executable the bat or bash file in the bin directory or run java -jar lib/interlok-boot.jar. Please note that on linux and mac you may need to make the bash file executable chmod +x ./start-interlok
* If you want to "run as Windows services" then we suggest using something like https://github.com/winsw/winsw to wrap the java process.
* You will have to explicitly choose all the optional components you want
* You will need internet access
