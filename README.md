tycho.xtext.mwe2.test
=====================

Shows a problem with exec-maven-plugin, tycho and access to external language in mwe2 workflow file.


Steps:
======

### 1. Increase memory.

```
   export MAVEN_OPTS="-Xmx512m -XX:MaxPermSize=256m"
```

### 2. Build the language

```
 mvn clean install
```


### 3. Observe console output
The console output should contain the following error:
```
[INFO] The project's OSGi version is 12.1.1.201401271120
[INFO] 
[INFO] --- tycho-packaging-plugin:0.19.0:validate-id (default-validate-id) @ tycho.xtext.mwe2.test.lang_b ---
[INFO] 
[INFO] --- tycho-packaging-plugin:0.19.0:validate-version (default-validate-version) @ tycho.xtext.mwe2.test.lang_b ---
[INFO] 
[INFO] >>> exec-maven-plugin:1.2.1:java (default) @ tycho.xtext.mwe2.test.lang_b >>>
[INFO] 
[INFO] --- tycho-packaging-plugin:0.19.0:build-qualifier (default-build-qualifier) @ tycho.xtext.mwe2.test.lang_b ---
[INFO] The project's OSGi version is 12.1.1.201401271120
[INFO] 
[INFO] --- tycho-packaging-plugin:0.19.0:validate-id (default-validate-id) @ tycho.xtext.mwe2.test.lang_b ---
[INFO] 
[INFO] --- tycho-packaging-plugin:0.19.0:validate-version (default-validate-version) @ tycho.xtext.mwe2.test.lang_b ---
[INFO] 
[INFO] <<< exec-maven-plugin:1.2.1:java (default) @ tycho.xtext.mwe2.test.lang_b <<<
[INFO] 
[INFO] --- exec-maven-plugin:1.2.1:java (default) @ tycho.xtext.mwe2.test.lang_b ---
0    [org.eclipse.emf.mwe2.launch.runtime.Mwe2Launcher.main()] INFO  lipse.emf.mwe.utils.StandaloneSetup  - Using resourceSet registry. The registered Packages will not be registered in the global EPackage.Registry.INSTANCE!
6    [org.eclipse.emf.mwe2.launch.runtime.Mwe2Launcher.main()] INFO  lipse.emf.mwe.utils.StandaloneSetup  - Registering platform uri 'D:\tmp\tycho.xtext.mwe2.test'
193  [org.eclipse.emf.mwe2.launch.runtime.Mwe2Launcher.main()] INFO  clipse.emf.mwe.utils.GenModelHelper  - Registered GenModel 'http://tycho.xtext.mwe2.test/Lang_A' from 'file:/D:/tmp/tycho.xtext.mwe2.test/tycho.xtext.mwe2.test.lang_b/../tycho.xtext.mwe2.test.lang_a/model/generated/Lang_A.genmodel'
196  [org.eclipse.emf.mwe2.launch.runtime.Mwe2Launcher.main()] ERROR mf.mwe2.launch.runtime.Mwe2Launcher  - Problems instantiating module tycho.xtext.mwe2.test.lang_b.GenerateLang_B: java.lang.reflect.InvocationTargetException
java.lang.RuntimeException: Problems instantiating module tycho.xtext.mwe2.test.lang_b.GenerateLang_B: java.lang.reflect.InvocationTargetException
        at org.eclipse.emf.mwe2.launch.runtime.Mwe2Runner.run(Mwe2Runner.java:95)
        at org.eclipse.emf.mwe2.launch.runtime.Mwe2Runner.run(Mwe2Runner.java:62)
        at org.eclipse.emf.mwe2.launch.runtime.Mwe2Runner.run(Mwe2Runner.java:52)
        at org.eclipse.emf.mwe2.launch.runtime.Mwe2Launcher.run(Mwe2Launcher.java:74)
        at org.eclipse.emf.mwe2.launch.runtime.Mwe2Launcher.main(Mwe2Launcher.java:35)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:601)
        at org.codehaus.mojo.exec.ExecJavaMojo$1.run(ExecJavaMojo.java:297)
        at java.lang.Thread.run(Thread.java:722)
Caused by: org.eclipse.emf.common.util.WrappedException: java.lang.reflect.InvocationTargetException
        at org.eclipse.emf.mwe2.language.factory.SettingProviderImpl$1$1.setValue(SettingProviderImpl.java:56)
        at org.eclipse.emf.mwe2.language.factory.Mwe2ExecutionEngine.internalApplyAssignments(Mwe2ExecutionEngine.java:143)
        at org.eclipse.emf.mwe2.language.factory.Mwe2ExecutionEngine.inCase(Mwe2ExecutionEngine.java:114)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:601)
        at org.eclipse.xtext.util.PolymorphicDispatcher.invoke(PolymorphicDispatcher.java:291)
        at org.eclipse.emf.mwe2.language.factory.Mwe2ExecutionEngine.internalSwitch(Mwe2ExecutionEngine.java:66)
        at org.eclipse.emf.mwe2.language.factory.Mwe2ExecutionEngine.internalApplyAssignments(Mwe2ExecutionEngine.java:142)
        at org.eclipse.emf.mwe2.language.factory.Mwe2ExecutionEngine.inCase(Mwe2ExecutionEngine.java:114)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:601)
        at org.eclipse.xtext.util.PolymorphicDispatcher.invoke(PolymorphicDispatcher.java:291)
        at org.eclipse.emf.mwe2.language.factory.Mwe2ExecutionEngine.internalSwitch(Mwe2ExecutionEngine.java:66)
        at org.eclipse.emf.mwe2.language.factory.Mwe2ExecutionEngine.inCase(Mwe2ExecutionEngine.java:80)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:601)
        at org.eclipse.xtext.util.PolymorphicDispatcher.invoke(PolymorphicDispatcher.java:291)
        at org.eclipse.emf.mwe2.language.factory.Mwe2ExecutionEngine.internalSwitch(Mwe2ExecutionEngine.java:66)
        at org.eclipse.emf.mwe2.language.factory.Mwe2ExecutionEngine.create(Mwe2ExecutionEngine.java:62)
        at org.eclipse.emf.mwe2.launch.runtime.Mwe2Runner.run(Mwe2Runner.java:93)
        ... 10 more
Caused by: java.lang.reflect.InvocationTargetException
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:601)
        at org.eclipse.emf.mwe2.language.factory.SettingProviderImpl$1$1.setValue(SettingProviderImpl.java:54)
        ... 35 more
Caused by: org.eclipse.emf.mwe.core.ConfigurationException: Couldn't find an interface tycho.xtext.mwe2.test.lang_a.lang_a.Lang_aPackage
        at org.eclipse.emf.mwe.utils.StandaloneSetup.addRegisterGeneratedEPackage(StandaloneSetup.java:414)
        ... 40 more
```