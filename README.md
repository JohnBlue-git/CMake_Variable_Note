# CMake_Variable_Note



# Cache variables

Cache variables in CMake have several properties that control their behavior. Here are some key properties:

Name: The name of the cache variable, which must be unique in the cache.

Value: The current value of the variable. This can be set to different types of values (e.g., string, boolean, integer).

Type: The type of the variable, typically STRING, BOOL, or PATH. This influences how the variable is presented in the CMake GUI and how it can be set.
TYPE: If not explicitly set, CMake will infer the type based on the initial value. However, setting it explicitly ensures that users and tools interact with the variable as intended.

Help String: A description of the variable's purpose, which appears in the CMake GUI to guide users.

Generator Expression: Sometimes used to generate or modify cache variables dynamically.

Set By User: Indicates whether the value was set by the user or is a default.

Internal: A property that can be set to ON to prevent the variable from appearing in the CMake GUI or during configuration.
INTERNAL: By default, cache variables are not internal. 

Advanced: Marks the variable as "advanced" so it won't appear in the CMake GUI unless the user explicitly requests to see advanced variables.

# non cache variable

Scope: They have local scope within the directory they are set and can be used by the current CMakeLists.txt file and its subdirectories. They do not persist across CMake runs.

Temporary: These variables are temporary and do not affect future CMake configurations. They are reset each time CMake is run.

Visibility: They are visible within the directory and its subdirectories but do not influence or interact with the top-level cache or other parts of the project beyond their immediate context.

No Cache Persistence: Since they are not stored in the cache, these variables do not retain their values between different CMake runs or configurations.

Usage: They are often used for intermediate values, configurations, or flags that are only relevant during the current CMake session.


# cache / global / local

once you configure and build a project with CMake at the top level, the variables in the cache are remembered across builds, including if you later run CMake at a subdirectory level. Here’s how it works:

Cache Variables: When you run CMake at the top level, it creates and updates the cache (CMakeCache.txt) with the variables and their values. These cache variables persist between builds and are reused in subsequent runs.

Subdirectory Builds: If you then configure or build a subdirectory independently, CMake will still reference the top-level cache if the top-level configuration is still valid. This is because CMake generally uses the cache and configuration from the initial top-level configuration.

Consistency: For consistent builds, it’s typically recommended to run cmake from the top level, especially when using cache variables. However, if you run CMake in a subdirectory and that subdirectory has its own CMakeLists.txt, it might not fully configure the project if it relies on top-level configurations or cache variables.

