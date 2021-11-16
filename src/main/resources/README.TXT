
To start the installer you will need to launch bin/interlok-installer.bat or bin/interlok-installer depending if you are on windows or linux/mac.
Use the property `interlokDistDirectory` to specify the directory where you want to install Interlok.

For example:
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
You need to uncomment the optional components you wish to install with Interlok.

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
