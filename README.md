# starter

[![Go](https://github.com/g41797/starter/actions/workflows/go.yml/badge.svg)](https://github.com/g41797/starter/actions/workflows/go.yml)

*starter* is part of [sputnik](https://github.com/g41797/sputnik#readme).
It's placed in the separate repository due to high requirements for golang version (1.21).

*"...Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application's services. Then, with a single command, you create and start all the services from your configuration..."*

*starter* performs functionality described above programmatically:
- store docker-compose.yml within configuration folder
```bash
./cmd/syslog-e2e/conf
├── blocks.json
├── connector.json
├── docker-compose.yml
├── syslogproducer.json
└── syslogreceiver.json
```
- import starter
```go
import (
    ..........................
    "github.com/g41797/starter"
    ..........................
)
```

- call starter from the very beginning 
```go
func main() {

	stop, err := starter.StartServices()

	if err != nil {
		fmt.Println(err)
		return
	}

	defer stop()

	sidecar.Start(new(adapter.BrokerConnector))
}
```
