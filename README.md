# fluxus

Fluxus is an ongoing-development software based on JAVA and MongoDB. It is conceived
to run business processes of any type. It is focused on simplicity rather than complex
BPM concepts but rather similar.

## State of the code

We are not even in alpha mode. This is currently the development of the program

## How to run the code

The program is a Spring Boot software. Then if you down load the source and run a
`maven build`, you will be able to run the code as a JAR file.

You need to have a running MongoDB database on the same machine (because the code
is using the local configuration) but you can modify this behaviour using the
Spring MongoDB declarations on the file `application.properties` or through the
variables passed by argument (see Spring Boot configuration for more details).

The mongoDB database name is "fluxus" by default. Collections and indexes are automatically
created at runtime through the Spring annotations then the first start of the application
can be a quite long.

The port 8080 is used as the client server. This is a very important information because
this server is used to validate some actions and then must be running correctly.

## The philosophy

The philosophy behind _fluxus_ is to be both flexible and to follow a stream of actions
like for classic BPM. But in addition, the business processes can be both technical ones
or functional ones (I mean can be processes fully automatic like backups or manual
like the validation of holidays by a collaborator).

We tried to use the same vocabulary than for BPM. For example, _lanes_ are very useful
to both show where the process is but also to create a queue. For example, a user can
be also a lane. This is true for Gary which is the responsible of a team and need to
validate the holidays of the team members.

## Vocabulary

- Business Process Definition: the definition of a business process. This is like a
class in the object-oriented languages. It defines the business process. Note the
same business process can have multiple versions. By convention, only the last version
is active.

- Business Process Version (or simply _version_): any process evolves and changes
in time. Then the version is the version of the Business Process Definition. There is
always one and only one version active for a definition.

- Business Process Instance: sometimes referred as just "business process" is the
business process. By instance, we mean the business process has been initiated and
he's running. A instance always refers to a Business Process Definition and a associated
version.

- Event: an event is something which creates a Business Process Instance or participate
to modify the status of an already business process instance. By definition, an event
is just something which run a task.

- Task: a task is an operation made in an instance of business process. The task can
be an automatic one (sending a file though FTP) or manual (the validation of the holidays
by the team's manager). A task can be waiting, running, done or failed.

- Lane: the lane is where the task is. For example, it can be a user or a service. This
information is mainly linked to statistics. Lanes are globals in the sense a lane can be
used by any number of business process definitions.




