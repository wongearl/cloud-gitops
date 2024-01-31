<!--
 Licensed to the Apache Software Foundation (ASF) under one
 or more contributor license agreements.  See the NOTICE file
 distributed with this work for additional information
 regarding copyright ownership.  The ASF licenses this file
 to you under the Apache License, Version 2.0 (the
 "License"); you may not use this file except in compliance
 with the License.  You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

 Unless required by applicable law or agreed to in writing,
 software distributed under the License is distributed on an
 "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
 KIND, either express or implied.  See the License for the
 specific language governing permissions and limitations
 under the License.
 -->

# Helm Chart for Amoro

[Amoro](https://amoro.netease.com) is a Lakehouse management system built on open data lake formats.
Working with compute engines including Flink, Spark, and Trino, Amoro brings pluggable and self-managed features for Lakehouse to provide out-of-the-box data warehouse experience, 
and helps data platforms or products easily build infra-decoupled, stream-and-batch-fused and lake-native architecture.


## Introduction

This chart will bootstrap an [Amoro](https://amoro.netease.com) deployment on a [Kubernetes](http://kubernetes.io)
cluster using the [Helm](https://helm.sh) package manager.

## Requirements

- Kubernetes cluster
- Helm 3.0+

## Template rendering

When you want to test the template rendering, but not actually install anything. [Debugging templates](https://helm.sh/docs/chart_template_guide/debugging/) provide a quick way of viewing the generated content without YAML parse errors blocking.

There are two ways to render templates. It will return the rendered template to you so you can see the output.

First of all, you should rebuild the charts/ directory based on the Chart.lock file.

```shell
helm dependency build
```

- Local rendering chart templates
```shell
helm template --debug ../amoro
```
- Server side rendering chart templates
```shell
helm install --dry-run --debug --generate-name ../amoro
```
<!-- ## Features -->

## Documentation

Configuration guide documentation for Amoro lives [on the website](https://amoro.netease.com/docs/latest). (Not just for Helm Chart)

## Contributing

Want to help build Amoro? Check out our [contributing documentation](https://amoro.netease.com/join-community).