# Gradle Issue #9796


This is a reproduce project for issue [gradle #9796](https://github.com/gradle/gradle/issues/9796)

## Details

The `producer` module contains a groovy global ASTTransformation which is registered by resources `META-INF/services/org.codehaus.groovy.transform.ASTTransformation`.

### Expected Behavior

In normal case, when executing ```./gradlew :consumer:compileGroovy```, groovy compiler can find the resources, execute the AST transforming and the output will contains ``global ast transformation works!``. 

You can comment the ``java-library`` plugin in ``producer/build.gradle`` to see the outputs.

### Current Behavior

No outputs like ``global ast transformation works!``.  
With ``java-library`` plugin alongside the `groovy` plugin, the compiling classpath doesn't contains the resources of the producer project.

I also print the classpath to show the differences in whether using the ``java-library`` plugins. 