Keycloak 4
========

Merge Master Test #3

Open Source Identity and Access Management for modern Applications and Services.

For more information about Keycloak visit [Keycloak homepage](http://keycloak.org) and [Keycloak blog](http://blog.keycloak.org).


How to build
--------

Ensure you have JDK 8 (or newer), Maven 3.1.1 (or newer) and Git installed

    java -version
    mvn -version
    git --version
    
First clone the Keycloak repository:
    
    git clone https://github.com/keycloak/keycloak.git
    cd keycloak
    
To build Keycloak run:

    mvn install
    
This will build all modules and run the testsuite. 

To build the distribution run:

    mvn install -Pdistribution
    
Once completed you will find distribution archives in `distribution`.

To build only the server run:

    mvn -Pdistribution -pl distribution/server-dist -am -Dmaven.test.skip clean install


Starting Keycloak
-----------------

To start Keycloak during development first build as specified above, then run:

    mvn -f testsuite/utils/pom.xml exec:java -Pkeycloak-server 

When running testsuite, by default an account with username `admin` and password `admin` will be created within the master realm at start.

To start Keycloak from the server distribution first build the distribution it as specified above, then run:

    tar xfz distribution/server-dist/target/keycloak-<VERSION>.tar.gz
    cd keycloak-<VERSION>
    bin/standalone.sh
    
To stop the server press `Ctrl + C`.

Reporting security vulnerabilities
----------------------------------

If you've found a security vulnerability, please look at the [instructions on how to properly report it](http://www.keycloak.org/security.html)

Help and Documentation
----------------------
* [Documentation](http://www.keycloak.org/documentation.html) - User Guide, Admin REST API and Javadocs
* [User Mailing List](https://lists.jboss.org/mailman/listinfo/keycloak-user) - Mailing list to ask for help and general questions about Keycloak
* [JIRA](https://issues.jboss.org/projects/KEYCLOAK) - Issue tracker for bugs and feature requests


Contributing
------------

* Developer documentation
    * [Hacking on Keycloak](misc/HackingOnKeycloak.md) - How to become a Keycloak contributor
    * [Testsuite](misc/Testsuite.md) - Details about testsuite, but also how to quickly run Keycloak during development and a few test tools (OTP generation, LDAP server, Mail server)
    * [Database Testing](misc/DatabaseTesting.md) - How to do testing of Keycloak on different databases
    * [Updating Database](misc/UpdatingDatabaseSchema.md) - How to change the Keycloak database
    * [Changing the Default keycloak-subsystem Configuration](misc/UpdatingServerConfig.md) - How to update the default keycloak-subsystem config
* [Developer Mailing List](https://lists.jboss.org/mailman/listinfo/keycloak-dev) - Mailing list to discuss development of Keycloak


License
-------

* [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)
KEYCLOAK-0019955
