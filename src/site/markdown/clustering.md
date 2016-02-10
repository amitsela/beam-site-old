<!--
  ~ Licensed to the Apache Software Foundation (ASF) under one or more
  ~ contributor license agreements.  See the NOTICE file distributed with
  ~ this work for additional information regarding copyright ownership.
  ~ The ASF licenses this file to You under the Apache License, Version 2.0
  ~ (the "License"); you may not use this file except in compliance with
  ~ the License.  You may obtain a copy of the License at
  ~
  ~      http://www.apache.org/licenses/LICENSE-2.0
  ~
  ~ Unless required by applicable law or agreed to in writing, software
  ~ distributed under the License is distributed on an "AS IS" BASIS,
  ~ WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  ~ See the License for the specific language governing permissions and
  ~ limitations under the License.
  -->

Cluster setup
=============

Context server relies on Elasticsearch to discover and configure its cluster. You just need to install multiple context
servers on the same network, and enable the discovery protocol in $MY_KARAF_HOME/etc/org.apache.unomi.persistence.elasticsearch.cfg file :

    discovery.zen.ping.multicast.enabled=true

All nodes on the same network, sharing the same cluster name will be part of the same cluster.

###Recommended configurations

It is recommended to have one node dedicated to the context server, where the other nodes take care of the
Elasticsearch persistence. The node dedicated to the context server will have node.data set to false.

#### 2 nodes  configuration
One node dedicated to context server, 1 node for elasticsearch storage.

Node A :

    node.data=true
    numberOfReplicas=0
    monthlyIndex.numberOfReplicas=0

Node B :

    node.data=false
    numberOfReplicas=0
    monthlyIndex.numberOfReplicas=0

#### 3 nodes configuration
One node dedicated to context server, 2 nodes for elasticsearch storage with fault-tolerance

Node A :

    node.data=false
    numberOfReplicas=1
    monthlyIndex.numberOfReplicas=1

Node B :

    node.data=true
    numberOfReplicas=1
    monthlyIndex.numberOfReplicas=1

Node C :

    node.data=true
    numberOfReplicas=1
    monthlyIndex.numberOfReplicas=1

### Specific configuration
If multicast is not allowed on your network, you'll need to switch to unicast protocol and manually configure the server IPs. This can be
done by disabling the elasticsearch automatic discovery in $MY_KARAF_HOME/etc/org.apache.unomi.persistence.elasticsearch.cfg :

    discovery.zen.ping.multicast.enabled=false


And then set the property discovery.zen.ping.unicast.hosts in $MY_KARAF_HOME/etc/elasticsearch.yml files :


    discovery.zen.ping.unicast.hosts: [‘192.168.0.1:9300', ‘192.168.0.2:9300']


More information and configuration options can be found at :
[https://www.elastic.co/guide/en/elasticsearch/reference/current/modules-discovery.html](https://www.elastic.co/guide/en/elasticsearch/reference/current/modules-discovery.html)
