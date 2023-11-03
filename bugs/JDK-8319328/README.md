# Example for reproducing JDK-8319328: Disabling the JavaScript JIT leads to Segfault

This example demonstrates the issue reported as [JDK-8319328](https://bugs.java.com/bugdatabase/view_bug?bug_id=JDK-8319328) where disabling the JavaScript JIT leads to a segmentation fault when using JavaFX with WebKit.

## Prerequisites
- JDK
- JavaFX SDK
- Maven

## Build the Example
To build the example, follow these steps:

```sh
git clone https://github.com/ddscharfe/examples
cd examples/bugs/JDK-8319328
mvn clean verify
```

## Reproduce the Bug
After building the example, run it with the following commands:
```sh
# Set the environment variable to disable the JavaScript JIT
export JavaScriptCoreUseJIT=0

# Run the Java application
java --module-path <path-to-javafx-sdk>/lib --add-modules javafx.controls,javafx.web -cp target/sample-1.0.0.jar org.openjfx.App
```

With JavaScriptCoreUseJIT set to 0, the example should exhibit the crash as described in the bug report. If the variable is not set, or if it is set to any value other than 0, the example should run without crashing.