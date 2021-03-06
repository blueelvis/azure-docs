---
title: Azure Service Fabric CLI- sfctl compose| Microsoft Docs
description: Describes the Service Fabric CLI sfctl compose commands.
services: service-fabric
documentationcenter: na
author: rwike77
manager: timlt
editor: ''

ms.assetid: 
ms.service: service-fabric
ms.devlang: cli
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: multiple
ms.date: 09/22/2017
ms.author: ryanwi

---
# sfctl compose
Create, delete, and manage Docker Compose deployments.

## Commands

|Command|Description|
| --- | --- |
|    create| Deploy a Service Fabric application from a Compose file.|
|    list  | Gets the list of compose deployments created in the Service Fabric cluster.|
|   remove| Deletes an existing Service Fabric compose deployment from cluster.|
|   status| Gets information about a Service Fabric compose deployment.|
|upgrade       | Starts upgrading a compose deployment in the Service Fabric cluster.|
|    upgrade-status| Gets details for the latest upgrade performed on this Service Fabric compose deployment.|


## sfctl compose create
Creates a Service Fabric compose deployment.

### Arguments

|Argument|Description|
| --- | --- |
| --file-path [Required]| Path to the target Docker Compose file.|
 |   --deployment-name  [Required]| The name of the deployment.|
|    --encrypted-pass             | Rather than prompting for a container registry password, use an already encrypted passphrase.|
|    --has-pass                   | Prompts for a password to the container registry.|
|    --timeout -t                 | Server time-out in seconds.  Default: 60.|
 |   --user                       | User name to connect to container registry.|

### Global Arguments

|Argument|Description|
| --- | --- |
| --debug                 | Increase logging verbosity to show all debug logs.|
| --help -h               | Show this help message and exit.|
| --output -o             | Output format.  Allowed values: json, jsonc, table, tsv.  Default:             json.|
| --query                 | JMESPath query string. For more information and examples, see http://jmespath.org/.|
| --verbose               | Increase logging verbosity. Use --debug for full debug logs.|

## sfctl compose list
Gets the list of compose deployments created in the Service Fabric cluster.

Gets the status about the compose deployments that were created or are in the process of being
        created in the Service Fabric cluster. The response includes the name, status, and other
        details about the compose deployment. If the deployments do not fit in a page, one page of
        results is returned as well as a continuation token, which can be used to get the next page.

### Arguments

|Argument|Description|
| --- | --- |
| --continuation-token| The continuation token parameter is used to obtain next set of results. A      continuation token with a non empty value is included in the response of      the API when the results from the system do not fit in a single response.      When this value is passed to the next API call, the API returns next set      of results. If there are no further results, then the continuation token      does not contain a value. The value of this parameter should not be URL      encoded.|
| --max-results    | The maximum number of results to be returned as part of the paged queries.      This parameter defines the upper bound on the number of results returned.      If      they do not fit in the message as per the max message size restrictions      defined in the configuration, the results returned can be less than the specified maximum results. If this parameter is zero or not specified,      the paged queries include as many results as possible that fit in the      return message.|
| --timeout -t     | Server time-out in seconds.  Default: 60.|

### Global Arguments

|Argument|Description|
| --- | --- |
| --debug          | Increase logging verbosity to show all debug logs.|
| --help -h        | Show this help message and exit.|
| --output -o      | Output format.  Allowed values: json, jsonc, table, tsv.  Default: json.|
| --query          | JMESPath query string. For more information and examples, see http://jmespath.org/.|
| --verbose        | Increase logging verbosity. Use --debug for full debug logs.|

## sfctl compose remove
Deletes an existing Service Fabric compose deployment from cluster.

Deletes an existing Service Fabric compose deployment. 

### Arguments

|Argument|Description|
| --- | --- |
| --deployment-name [Required]| The identity of the deployment. This is typically the full name of             the application without the 'fabric:' URI scheme.|
| --timeout -t            | Server time-out in seconds.  Default: 60.|

### Global Arguments

|Argument|Description|
| --- | --- |
| --debug                 | Increase logging verbosity to show all debug logs.|
| --help -h               | Show this help message and exit.|
| --output -o             | Output format.  Allowed values: json, jsonc, table, tsv.  Default:             json.|
| --query                 | JMESPath query string. For more information and examples, see http://jmespath.org/.|
| --verbose               | Increase logging verbosity. Use --debug for full debug logs.|

## sfctl compose status
Gets information about a Service Fabric compose deployment.

Returns the status of compose deployment that was created or in the process of being
        created in the Service Fabric cluster and whose name matches the one specified as the
        parameter. The response includes the name, status, and other details about the application.

### Arguments

|Argument|Description|
| --- | --- |
| --deployment-name [Required]| The identity of the deployment. |
| --timeout -t            | Server time-out in seconds.  Default: 60.|

### Global Arguments

|Argument|Description|
| --- | --- |
| --debug                 | Increase logging verbosity to show all debug logs.|
| --help -h               | Show this help message and exit.|
| --output -o             | Output format.  Allowed values: json, jsonc, table, tsv.  Default:             json.|
| --query                 | JMESPath query string. For more information and examples, see http://jmespath.org/.|
| --verbose               | Increase logging verbosity. Use --debug for full debug logs.|

## sfctl compose upgrade
Starts upgrading a compose deployment in the Service Fabric cluster.

Validates the supplied upgrade parameters and starts upgrading the deployment.

### Arguments
|Argument|Description|
| --- | --- |
|    --file-path        [Required]| Path to the target Docker Compose file.|
|    --deployment-name  [Required]| The name of the deployment.|
|    --default-svc-type-health-map| JSON encoded dictionary that describes the health policy used to                                   evaluate the health of services.|
|    --encrypted-pass             | Rather than prompting for a container registry password, use an                                   already encrypted passphrase.|
 |   --failure-action             | Possible values include: 'Invalid', 'Rollback', 'Manual'.|
|    --force-restart              | Force restart.|
 |   --has-pass                   | Prompts for a password to the container registry.|
|    --health-check-retry         | Health check retry time-out measured in milliseconds.|
|    --health-check-stable        | Health check stable duration measured in milliseconds.|
|    --health-check-wait          | Health check wait duration measured in milliseconds.|
|    --replica-set-check          | Upgrade replica set check time-out measured in seconds.|
|    --svc-type-health-map        | JSON encoded list of objects that describe the health policies                                   used to evaluate the health of different service types.|
|    --timeout -t                 | Server time-out in seconds.  Default: 60.|
|    --unhealthy-app              | The maximum allowed percentage of unhealthy applications before                                   reporting an error.        For example, to allow 10% of applications to be unhealthy, this value would be 10. The        percentage represents the maximum tolerated percentage of applications that can be unhealthy        before the cluster is considered in error. If the percentage is respected but there is at        least one unhealthy application, the health is evaluated as Warning. This percentage is calculated by        dividing the number of unhealthy applications over the total number of application instances        in the cluster.|
|    --upgrade-domain-timeout     | Upgrade domain time-out measured in milliseconds.|
|    --upgrade-kind               | Default: Rolling.|
|    --upgrade-mode               | Possible values include: 'Invalid', 'UnmonitoredAuto',                                   'UnmonitoredManual', 'Monitored'.  Default: UnmonitoredAuto.|
|    --upgrade-timeout            | Upgrade time-out measured in milliseconds.|
|    --user                       | User name to connect to container registry.|
|    --warning-as-error           | Warnings are treated with the same severity as errors.|

### Global Arguments
 |Argument|Description|
| --- | --- |
|   --debug                      | Increase logging verbosity to show all debug logs.|
|    --help -h                    | Show this help message and exit.|
 |   --output -o                  | Output format.  Allowed values: json, jsonc, table, tsv.
                                   Default: json.|
 |   --query                      | JMESPath query string. See http://jmespath.org/ for more                                   information and examples.|
 |   --verbose                    | Increase logging verbosity. Use --debug for full debug logs.|

## Next steps
- [Set up](service-fabric-cli.md) the Service Fabric CLI.
- Learn how to use the Service Fabric CLI using the [sample scripts](/azure/service-fabric/scripts/sfctl-upgrade-application).