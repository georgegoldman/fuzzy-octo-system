# fuzzy-octo-system

**CMake syntax**

List the dependencies and prerequisites needed to run your project.

```bash
# Example for installing required packages on Ubuntu
sudo apt-get install -y cmake g++ 

```
## Commands

These are provided by CMake and are the essential building blocks of the DSL, as they allow you to manipulate variables. They include control flow constructs and the target_* family of commands. You can find a complete list of available commands with:

**This command combo get the you the insight to "PROJECT_BINARY_DIR" function**
```
cmake --help-variable PROJECT_BINARY_DIR
```

**This will print list of in built command in cmake**

```
cmake --help-command-list
```

## Modules

These are collections of functions and macros and are either CMake- or user-defined. CMake comes with a rich ecosystem of modules and you will probably write a few of your own to encapulate frequently used functions or macros in your CMake scripts. You will have to include the module to use its contents, for example:

**The full list of built-in modules is available with:**
```
$ cmake --help-module-list
```
**Help on a specific built-in module can be obtained with:**
```
$ cmake --help-module CMakePrintHelpers
```

## Flow control

