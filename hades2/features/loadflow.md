---
title: Hades - LoadFlow
layout: default
---

# Configuration
To use Hades for load-flow computations, set the `LoadFlowFactory` property of the
[componentDefaultConfig](http://powsybl.github.io/docs/configuration/modules/componentDefaultConfig.html) module to
`com.rte_france.powsybl.hades2.Hades2Factory`

To setup Hades, configure the [hades2](../configuration/hades2.md) module.

## YAML
```yaml
componentDefaultConfig:
    LoadFlowFactory: com.rte_france.powsybl.hades2.Hades2Factory
    
hades2:
    homeDir: /home/user/hades2-V5.5.1.2
    debug: false
    useSax: true
```

## XML
```xml
<config>
    <componentDefaultConfig>
        <LoadFlowFactory>com.rte_france.powsybl.hades2.Hades2Factory</LoadFlowFactory>
    </componentDefaultConfig>
    
    <hades2>
        <homeDir>/home/user/hades2-V5.5.1.2</homeDir>
        <debug>false</debug>
        <useSax>true</useSax>
    </hades2>
</config>
```

# Examples
The following example shows how to run a [load flow](http://powsybl.github.io/docs/tools/loadflow.html), using Hades and default configuration:
```shell
$> itools loadflow --case-file case.xiidm
Loading network 'case.xiidm'
loadflow results:
+--------+-----------------------------------------------------------------------------------------+
| Result | Metrics                                                                                 |
+--------+-----------------------------------------------------------------------------------------+
| true   | {nbIter=4, dureeCalcul=0.006098, cause=0, contraintes=6, statut=OK, csprMarcheForcee=0} |
+--------+-----------------------------------------------------------------------------------------+
```

The following example shows how to run a load flow, using Hades and a [specific parameters](../configuration/ADNLoadFlowParameters.md)
file:
```shell
$> itools loadflow --case-file case.xiidm --parameters-file hades-lf-parameters.json
Loading network 'case.xiidm'
loadflow results:
+--------+-----------------------------------------------------------------------------------------+
| Result | Metrics                                                                                 |
+--------+-----------------------------------------------------------------------------------------+
| true   | {nbIter=4, dureeCalcul=0.006377, cause=0, contraintes=6, statut=OK, csprMarcheForcee=0} |
+--------+-----------------------------------------------------------------------------------------+
```