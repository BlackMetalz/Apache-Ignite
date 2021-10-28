## -- Demo config
- Other example: https://github.com/apache/ignite/blob/master/examples/config/example-default.xml

In this config. I did change port 47500 ( discovery ) --> 8100. Port 47100 ( communication ) -> 8101

```
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="
       http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd">

      <bean class="org.apache.ignite.configuration.IgniteConfiguration">
      <property name="discoverySpi">
            <bean class="org.apache.ignite.spi.discovery.tcp.TcpDiscoverySpi">
            <property name="localPort" value="8100"/>
            <property name="ipFinder">
                <bean class="org.apache.ignite.spi.discovery.tcp.ipfinder.vm.TcpDiscoveryVmIpFinder">
                    <property name="addresses">
                        <list>
                            <!--
                              Explicitly specifying address of a local node to let it start and
                              operate normally even if there is no more nodes in the cluster.
                              You can also optionally specify an individual port or port range.
                              -->
                            <!-- <value>1.2.3.4</value> -->
                            <!--
                              IP Address and optional port range of a remote node.
                              You can also optionally specify an individual port.
                              -->
                            <value>10.3.48.54:8100</value>
                            <value>10.3.48.56:8100</value>
                            <value>10.3.48.82:8100</value>
                        </list>
                    </property>
                </bean>
          </property>
          </bean>
          </property>


    <!--
    Explicitly configure TCP communication SPI changing local
    port number for the nodes from the first cluster.
    -->

    <property name="communicationSpi">
        <bean class="org.apache.ignite.spi.communication.tcp.TcpCommunicationSpi">
            <property name="localPort" value="8101"/>
        </bean>
    </property>

    </bean>


</beans>

```

