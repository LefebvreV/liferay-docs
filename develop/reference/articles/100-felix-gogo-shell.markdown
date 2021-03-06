# Felix Gogo Shell [](id=using-the-felix-gogo-shell)

To interact with @product@'s module framework on a local server machine, you can
leverage a local telnet session:

    telnet localhost 11311

Running this command requires a local running instance of @product@ and your
machine's telnet command line utilities enabled.

To disconnect the session, execute the `disconnect` command. 

**Warning**: Commands  `shutdown`, `close`, and `exit` stop the OSGi framework.
So make sure to use the `disconnect` command to end the telnet Gogo Shell
session. 

If you have [Blade CLI](/develop/tutorials/-/knowledge_base/7-1/blade-cli)
installed, you can run the Felix Gogo shell via Blade command:

    blade sh <gogoShellCommand>

Here are some useful Gogo shell commands:

`b [BUNDLE_ID]`: lists information about a specific bundle including the
bundle's symbolic name, bundle ID, data root, registered (provided) and used
services, imported and exported packages, and more

`diag [BUNDLE_ID]`: lists information about why the specified bundle is not
working (e.g., unresolved dependencies, etc.)

`headers [BUNDLE_ID]`: lists metadata about the bundle from the bundle's
`MANIFEST.MF` file

`help`: lists all the available Gogo shell commands. Notice that each command
has two parts to its name, separated by a colon. For example, the full name of
the `help` command is `felix:help`. The first part is the command scope while
the second part is the command function. The scope allows commands with the same
name to be disambiguated. E.g., scope allows the `felix:refresh` command to be
distinguished from the `equinox:refresh` command.

`help [COMMAND_NAME]`: lists information about a specific command including a
description of the command, the scope of the command, and information about any
flags or parameters that can be supplied when invoking the command.

`inspect capability service [BUNDLE_ID]`: lists services exposed by a bundle

`install [PATH_TO_JAR_FILE]`: installs the specified bundle into Liferay's
module framework

`lb`: lists all of the bundles installed in Liferay's module framework. Use
the `-s` flag to list the bundles using the bundles' symbolic names.

`packages [PACKAGE_NAME]`: lists all of the named package's dependencies 

`scr:list`: lists all of the components registered in the module framework
(*scr* stands for service component runtime)

`scr:info [COMPONENT_NAME]`: lists information about a specific component
including the component's description, services, properties, configuration,
references, and more.

`services`: lists all of the services that have been registered in Liferay's
module framework

`start [BUNDLE_ID]`: starts the specified bundle

`stop [BUNDLE_ID]`: stops the specified bundle

`system:getproperties`: lists all of the system properties

`uninstall [BUNDLE_ID]`: uninstalls the specified bundle from Liferay's module
framework

For more information about the Gogo shell, visit
[Apache's official documentation](http://felix.apache.org/documentation/subprojects/apache-felix-gogo.html).
