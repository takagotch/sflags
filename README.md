### sflags
---
https://github.com/octago/sflags

```go
type HTTPConfig struct {
  Host string `desc:"HTTP host"`
  Port int `flag:"port p" desc:"some port"`
  SSL bool `env:"HTTP_SSL_VALUE"`
  Timeout time.Duration `flag:",deprecated,hidden"`
}

type Config struct {
  HTTP HTTPConfig
  Stats StatsConfig
}

package main

import (
  "flag"
  "log"
  "time"
  
  "github.com/octago/sflags/gen/gflag"
)

type httpConfig struct {
  Host string `desc:"HTTP host"`
  Port int
  SSL bool
  Timeout time.Duration
}

type config struct {
  HTTP httpConfig
}

func main() {
  cfg := &config{
    HTTP: httpConfig{
      Host: "127.0.0.1",
      Port: 6000,
      SSL: false,
      Timeout: 15 * time.Second,
    },
  }
  err := gflag.ParseToDef(cfg)
  if err != nil {
    log.Fatalf("err: %v", err)
  }
  flag.Parse()
}

```

```
go run ./main.go --help
```

```
```


