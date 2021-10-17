# JVisualVM Notes

To remotely connect to a JVM application using JVisualVM, add following arguments:

```
java \
-Dcom.sun.management.jmxremote \ 
-Dcom.sun.management.jmxremote.rmi.port=portExposed \ 
-Dcom.sun.management.jmxremote.port=portExposed \ 
-Dcom.sun.management.jmxremote.authenticate=false \
-Dcom.sun.management.jmxremote.ssl=false \ 
-Dcom.sun.management.jmxremote.local.only=false \ 
-Djava.rmi.server.hostname=IpOfHost \
-jar yourApp.jar
```

For example, 

```
java \
-Dcom.sun.management.jmxremote \
-Dcom.sun.management.jmxremote.rmi.port=7011 \
-Dcom.sun.management.jmxremote.port=7011 \
-Dcom.sun.management.jmxremote.authenticate=false \
-Dcom.sun.management.jmxremote.ssl=false \
-Dcom.sun.management.jmxremote.local.only=false \
-Djava.rmi.server.hostname=192.168.10.128 \
-jar -Xmx500m auth-service-web-1.0.0.jar \
--spring.profiles.active=test \
--dubbo.protocol.port=-1 \
--server.port=8084
```

Just make sure that following arguments are specified before `-jar`:

- -Dcom.sun.management.jmxremote
- -Dcom.sun.management.jmxremote.rmi.port=`[port_exposed]`
- -Dcom.sun.management.jmxremote.port=`[port_exposed]`
- -Dcom.sun.management.jmxremote.authenticate=false
- -Dcom.sun.management.jmxremote.ssl=false
- -Dcom.sun.management.jmxremote.local.only=false 

Then in JVisualVM: 

1. Select `Add Remote Host` and enter the ip address of the application
2. Select `Add JMX Connection` and enter the port that you specified above in those JVM arguments

