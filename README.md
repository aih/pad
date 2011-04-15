# About Etherpad
EtherPad is a web-based realtime collaborative document editor.

Instructions from Etherpad wiki on Google Code:

Welcome to open sourced EtherPad!

This file contains instructions for compiling and running the etherpad open source release. The steps have been tested on MacOS X and Linux. Windows users will probably want to grab Cygwin.

Requirements
Java 1.6 (tested with 1.6.0_10)
Scala 2.7 (tested with 2.7.4)
MySQL Server 5.1 (tested with 5.1.41)
mysql-connector-java (tested with 5.1.0)
Environment
Various scripts make assumptions about environment variables:

JAVA should be set to the java executable.
JAVA_HOME should be set to the main jdk directory.
SCALA should be set to the scala executable.
SCALA_HOME should be set to the main scala distribution directory.
PATH should contain $JAVA, $SCALA, and mysql
MYSQL_CONNECTOR_JAR should be set to the mysql-connector JAR file included in the mysql-connector download.
For example, this sets up the environment on my machine:

export JAVA_HOME="/usr/local/java/jdk1.6.0_10"
export SCALA_HOME="/usr/local/scala/scala-2.7.4.final"
export JAVA="$JAVA_HOME/bin/java"
export SCALA="$SCALA_HOME/bin/scala"
export PATH="$JAVA_HOME/bin:$SCALA_HOME/bin:/usr/local/mysql/bin:$PATH"
export MYSQL_CONNECTOR_JAR="/Aaron/lib/mysql-connector-java-5.1.10-bin.jar"
Database Setup
The scripts assume mysqld is running on localhost. Once mysqld is running, you can set up the etherpad database by running the following command inside ajcode/etherpad/.

$ sudo bin/setup-mysql-db.sh
This will create a database called "etherpad" with the password "password", and grant privileges to the user "etherpad".

All the tables will be set up the first time etherpad is run.

Compiling
EtherPad compiles all its Java and Scala libraries into a single JAR. To build this jar, you can run the following command inside ajcode/etherpad/.

$ bin/rebuildjar.sh
If you modify anything in ajcode/infrastructure, you will most likely need to kill the server, rebuild the jar, and re-launch the server before your change takes effect.

Code inside ajcode/etherpad/src can be modified while the server is running, and the changes will automatically get picked up.

Running
To run the etherpad web server, execute the following command inside ajcode/etherpad/.

$ bin/run-local.sh
The first time you run this, it should print out lots of messages about database migrations and finally print:

HTTP server listening on http://localhost:9000/
At this point, you should be able to visit http://localhost:9000/ in your web browser and create a new pad.

Support
Please use this google group to ask questions about the code. You may also want to consult the KnownIssues.
