# Betalink Logger

``Betalink-logger`` is the logger used in the different microservices of the betalink infrastructure. It provides customizable logging for applications. It supports multiple logging levels, file outputs, system logs, and concurrent-safe operations. The library is designed to be extensible and integrates seamlessly with both stdout and syslog.

## Features

- Multiple Log Levels:
    - ``Info`` (INFO)
    - ``Warning`` (WARN)
    - ``Error`` (ERROR)
    - ``Fatal`` (FATAL), which exits the program after logging.
- Custom Output Streams: Write logs to files, system log, stdout, or stderr.
- Concurrency-Safe Logging: Thread-safe operations with sync.Mutex.
- Configurable Logging Behavior: Enable or disable verbose logging for finer control.
- Graceful Closing: Ensures all log writers are properly closed to avoid data loss.

## Installation

```shell
go get github.com/BragdonD/betalink-logger
```

## Usage

```go
package main

import (
	"os"

	"github.com/BragdonD/betalink-logger"
)

func main() {
	// Initialize logger with file output
	logFile, _ := os.Create("app.log")
	logger := betalinklogger.NewLogger("MyApp", true, false, logFile)

	defer logger.Close()

	// Log messages with different severity levels
	logger.Info("This is an informational message.")
	logger.Warning("This is a warning.")
	logger.Error("This is an error.")
}
```

## Contributing

Feel free to open issues or submit pull requests for enhancements or bug fixes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
