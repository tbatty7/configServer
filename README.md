To test config server:
- Start it up with `.gradlew bootrun`
- In console, curl it with `curl http://root:s3cr3t@localhost:8888/config-client/test/master
`
- This should return a property of {"test":"dev"}

This application is tied to my repo called config-server-properties.
That holds the properties files.
The client application consuming this config server is in my repo called
configClient.

In my config properties repo that this is wired to, it has a folder named 
config-client, which is also the name of my client application if you look
in my configClient repo in the bootstrap.properties file in src/main/resources.

This allows you to have a common config-server that holds properties
files for every app, with each app's properties files in a folder named
after the app name that is passed when the request is made.  The key is the
pattern matcher property of `spring.cloud.config.server.git.searchPaths={application}`
