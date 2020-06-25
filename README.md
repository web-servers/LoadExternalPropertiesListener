# LoadExternalPropertiesListener
Sources of the JWS tomcat extension properties Listener.

The Load External Properties Lifecycle Listener loads
    properties files specified by the listener's <code>file.N</code> attributes
    in the server.xml.
# building
```
mvn install
cp target/LoadExternalPropertiesListener-1.0-SNAPSHOT.jar ${CATALINA_BASE}/lib
```

# Configuration in server.xml
Load External Properties Lifecycle Listen

The listener must be nested within a <code>Server</code>
element, and it is recommended that this listener be the first nested element in the <code>Server</code>.
XML is processed in the order it appears, and defining this listener first allows properties to
be defined and used later in the file.


The following additional attributes are supported by the <strong>Load External Properties Lifecycle Listener</strong>:

#    attribute name="file.N" required="true"

External files to include. This is a special attribute that uses a dynamic name, allowing for up to 100 files include with values for N
ranging from 0 to 99. Any values beyond 99 will result in files not being included and a warning being logged. These files will be loaded
in order based on the index, N.


For example, you could add two file attributes to the listener such as:

        <code>file.0="/path/to/file1.properties"
        file.1="/path/to/file2.properties"</code>

#      attribute name="overwrite" required="false"

Controls if previously defined system properties may be ovewritten. The default behavior is <code>true</code>, allowing for overwriting system properties.

#      attribute name="loadFirst" required="false"

Determines if any specified external files will be loaded before the rest of <code>server.xml</code>. The default is <code>false</code>,
indicating that the contents of <code>server.xml</code> will be loaded and procesed before external files.
