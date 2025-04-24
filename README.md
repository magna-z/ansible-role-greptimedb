greptimedb
---

Configure and run GreptimeDB as Docker container in systemd.service.


### Links
- <https://greptime.com>
- <https://github.com/GreptimeTeam/greptimedb>
- <https://hub.docker.com/r/greptime/greptimedb>


### Arguments
See [meta/argument_specs.yml](meta/argument_specs.yml).


### Examples
```yaml
greptimedb_docker_image: greptime/greptimedb:v0.13.2
greptimedb_docker_network: host
greptimedb_log_level: error
greptimedb_mode: standalone
greptimedb_config: |
  [http]
  enable_cors = false

  [grpc]
  bind_addr = "0.0.0.0:4001"
  runtime_size = 1
  [grpc.tls]
  mode = "disable"

  [mysql]
  enable = true
  addr = "0.0.0.0:4002"
  runtime_size = 1
  keep_alive = "0s"
  [mysql.tls]
  mode = "disable"

  [postgres]
  enable = true
  addr = "0.0.0.0:4003"
  runtime_size = 1
  [postgres.tls]
  mode = "disable"

  [opentsdb]
  enable = false

  [influxdb]
  enable = false

  [jaeger]
  enable = false

  [prom_store]
  enable = true
  with_metric_engine = true

  [storage]
  type = "File"
  data_home = "./data"

  [wal]
  provider = "raft_engine"
  dir = "./wal"
```


### Acknowledgement
- Ansible role uses [GreptimeDB](https://greptime.com) artifacts as main dependency.
