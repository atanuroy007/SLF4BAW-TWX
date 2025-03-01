# Atanu Logging Framework - Usage Guide

## Installation and Configuration Guide

### 1. Download the Toolkit

Download the latest version of the Advanced Java Logging Framework for IBM BAW from the GitHub repository:
https://github.com/atanuroy007/SLF4BAW

### 2. Add the Toolkit Dependency to Your Process Apps

Include the toolkit JAR (or Maven dependency) in your IBM BAW process app. Ensure that your process app's classpath includes the toolkit so that you can access the logging framework classes.

### 3. Use the Logger in Your Service Flows

Once the dependency is added, you can start using the logger in your IBM BAW service flows. For example:

```javascript
SLF4BAW.info("This is an INFO log from BAW");
SLF4BAW.error("This is an ERROR log from BAW");
SLF4BAW.debug("This is a DEBUG log from BAW");
```

These methods will log messages at the appropriate levels, allowing you to track and debug your process app flows effectively.

### 4. Configuration

The logging framework is fully configurable via toolkit environment variables. The default log location is:

```
node_profile_root/logs/CustomLogger
```

When used within a process app, a subfolder will be created under this directory corresponding to the process app name. Within each process app's folder, separate log files are generated for each log level. Log files are automatically rolled based on the configured size, and old files are deleted when the total log size for the process app exceeds the configured cap.

**Sample Folder and File Structure:**

```
node_profile_root/
└── logs/
    └── CustomLogger/
        ├── MyProcessApp/
        │   ├── info.log      // INFO level logs
        │   ├── debug.log     // DEBUG level logs
        │   └── error.log     // ERROR level logs
        └── FrameworkLogs/
            ├── framework.log // Logs for framework-level events
            └── trace.log     // Logs for tracing framework issues
```

You can modify these settings by updating the corresponding environment variables provided with the toolkit. This allows you to tailor the logging behavior (such as log file locations, sizes, patterns, and retention policies) to your specific deployment requirements.
