# OpenShift WildFly Cartridge

This cartridge is running WildFly 8.0.1.SNAPSHOT from the HornetQ Wildfly fork and uses the HornetQ snapshot

This cartridge is based on the JBoss AS cartridge found in OpenShift Origin [here](https://github.com/openshift/origin-server/tree/master/cartridges/openshift-origin-cartridge-jbossas).  



You can build a gear using this cartridge with the following command:

	rhc app create -s wildfly https://cartreflect-claytondev.rhcloud.com/reflect?github=hornetq/openshift-wildfly-cartridge
	
We need the '-s' as ot needs to be scalable


It will take a few minutes to build, so be patient.

If you want to upgrade the HornetQ version simply build the HQ Wildfly branch and overlay it over versions/8 directory and commit.

### JBoss CLI

This cartridge provides an OpenShift compatible wrapper of the JBoss CLI tool on the gear PATH, located at $OPENSHIFT_WILDFLY_DIR/bin/tools/jboss-cli.sh. Use the following command to connect to the WildFly instance with the CLI tool:

        jboss-cli.sh -c --controller=$OPENSHIFT_WILDFLY_IP:$OPENSHIFT_WILDFLY_MANAGEMENT_HTTP_PORT

###Super Secret Hint (Don't tell anyone)

If you run the rhc port-forward command, you can access the WildFly management interface on port 9990  
A username and password is created when you install this cartridge.  
If you don't write it down, fear not, the following environment variables will contain them.  
$OPENSHIFT_WILDFLY_USERNAME  
$OPENSHIFT_WILDFLY_PASSWORD

	corey$ rhc port-forward wildfly
	Checking available ports ... done
	Forwarding ports ...

	To connect to a service running on OpenShift, use the Local address

	Service Local               OpenShift
	------- -------------- ---- -------------------
	java    127.0.0.1:8080  =>  127.13.118.129:8080
	java    127.0.0.1:9990  =>  127.13.118.129:9990
	java    127.0.0.1:9999  =>  127.13.118.129:9999
	
In this example you would visit 127.0.0.1:9990 to view the wildfly admin panel from your local computer.


