# Fixed by https://github.com/FabricMC/fabric-loom/pull/791

# Fabric Kapt Issue

When gradle build with kapt it will 👇
```
* What went wrong:
Execution failed for task ':compileJava'.
> Multiple output file properties with name 'mixin-ap-main'
```

Caused by Java and Kapt add property twice
https://github.com/FabricMC/fabric-loom/blob/dev/1.0/src/main/java/net/fabricmc/loom/configuration/CompileConfiguration.java#L262-L277
```
passMixinArguments:98, AnnotationProcessorInvoker (net.fabricmc.loom.build.mixin)
configureMixin:147, AnnotationProcessorInvoker (net.fabricmc.loom.build.mixin)
configureMixin:76, KaptApInvoker (net.fabricmc.loom.build.mixin)
setupMixinAp:271, CompileConfiguration (net.fabricmc.loom.configuration)
```
```
passMixinArguments:98, AnnotationProcessorInvoker (net.fabricmc.loom.build.mixin)
configureMixin:147, AnnotationProcessorInvoker (net.fabricmc.loom.build.mixin)
setupMixinAp:262, CompileConfiguration (net.fabricmc.loom.configuration)
```
