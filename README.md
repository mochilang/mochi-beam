# mochi-beam

Mochi+Erlang/OTP bidirectional package bridge (MEP-66).

This repository contains the Go implementation of the Erlang bridge extracted
from the [mochi](https://github.com/mochilang/mochi) monorepo.

## Packages

| Package | Description |
|---------|-------------|
| `etf` | Erlang External Term Format encoder/decoder |
| `hexsemver` | Hex.pm-flavoured semver parser |
| `hexindex` | Hex.pm HTTP API v2 client + content-addressed cache |
| `beamingest` | BEAM file parser + Dbgi/Abst chunk reader |
| `edocingest` | EDoc XML fallback parser |
| `typemap` | Dialyzer typespec-to-Mochi type table + SkipReport |
| `portemit` | shim.erl gen_server emitter |
| `externemit` | shim.mochi extern fn/type emitter |
| `errors` | SkipReason + BridgeError |
| `build` | rebar3 workspace synthesis + build driver |
| `port` | Go-side OTP Port process manager |
| `lockfile` | mochi.lock [[erlang-package]] integration + --check mode |
| `target` | TargetErlangPort rebar3 app skeleton emitter |
| `publish` | Hex.pm OIDC trusted-publishing flow |
| `otp` | OTP behavior bindings: GenServer, Supervisor, Application |
| `async` | Async process bridge: Spawn, Send, Monitor, Mailbox |
| `cnode` | Distributed C-node: EPMD client + dist handshake + REG_SEND |

## Usage

```go
import "github.com/mochilang/mochi-beam/etf"
import "github.com/mochilang/mochi-beam/port"
import "github.com/mochilang/mochi-beam/otp"
import "github.com/mochilang/mochi-beam/cnode"
```

## Running tests

```
go test ./...
```

## Design

See MEP-66 in the mochi monorepo for the full specification. The bridge supports two directions:

- **Direction 1**: Mochi calls Erlang packages via a Port process (rebar3 + gen_server shim)
- **Direction 2**: Mochi publishes as a Hex.pm package (OIDC trusted publishing)
