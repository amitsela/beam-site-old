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
  
# About Beam 

Apache Beam is an open source, unified model and set of language-specific SDKs for defining and executing data processing workflows, and also data ingestion and integration flows, supporting Enterprise Integration Patterns (EIPs) and Domain Specific Languages (DSLs). Dataflow pipelines simplify the mechanics of large-scale batch and streaming data processing and can run on a number of runtimes like Apache Flink, Apache Spark, and Google Cloud Dataflow (a cloud service). Beam also brings DSL in different languages, allowing users to easily implement their data integration processes.

>The Apache Beam project is in the process of bootstrapping. This includes the creation of project resources, the refactoring of
 the initial code submission, and the formulation of project documentation, planning, and design documents. For more information about Beam see the [getting started](getting-started.html) page.

### Using Apache Beam 

You can use Beam for nearly any kind of data processing task, including both batch and streaming data processing.
Beam provides a unified data model that can represent any size data set, including an unbounded or infinite data
set from a continuously updating data source such as Kafka.

In particular, Beam pipelines can represent high-volume computations, where the steps in your job need to process an amount of data
that exceeds the memory capacity of a cost-effective cluster. Beam is particularly useful for [Embarrassingly Parallel](http://en.wikipedia.org/wiki/Embarassingly_parallel)
data processing tasks, in which the problem can be decomposed into many smaller bundles of data that can be processed
independently and in parallel.

You can also use Beam for Extract, Transform, and Load (ETL) tasks and pure data integration. These tasks are useful
for moving data between different storage media and data sources, transforming data into a more desirable format,
or loading data onto a new system.

### Programming Model

Beam provides a simple and elegant [programming model](https://cloud.google.com/dataflow/model/programming-model) to express your data processing jobs.
Each job is represented by a data processing pipeline that you create by writing a program with Beam. Each pipeline
is an independent entity that reads some input data, performs some transforms on that data to gain useful or
actionable intelligence about it, and produces some resulting output data. A pipeline's transform might include
filtering, grouping, comparing, or joining data.

Beam provides several useful abstractions that allow you to think about your data processing pipeline in a simple,
logical way. Beam simplifies the mechanics of large-scale parallel data processing, freeing you from the need
to manage orchestration details such as partitioning your data and coordinating individual workers.

### Key concepts

 * _Simple data representation_. Beam uses a specialized collection class, called PCollection, to represent your
pipeline data. This class can represent data sets of virtually unlimited size, including bounded and unbounded
data collections.
 * _Powerful data transforms_. Beam provides several core data transforms that you can apply to your data. These
transforms, called PTransforms, are generic frameworks that apply functions that you provide across an entire data
set.
 * _I/O APIs for a variety of data formats_. Beam provides APIs that let your pipeline read and write data to and
from a variety of formats and storage technologies. Your pipeline can read text files, Avro files, and more.

See the [programming model documentation](programming-model.html) to learn more about how Beam implements these
concepts.

### News
| **Date**  | **Event** |
|---|---|
| 2016-02-11 | Website created |
| 2016-02-02 | JIRA, mailing lists, git, website space created |
| 2016-02-01 | Project entered incubation |

### Apache project

Beam is an [Apache Software Foundation](http://www.apache.org) project, available under the Apache v2 license.
