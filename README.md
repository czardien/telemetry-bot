# Telemetry Bot
A telemetry exporter that scrapes Prometheus `/metrics` endpoints
and Jaeger api and exports timeseries to TimescaleDB.

![Fact Core](doc/bot.png)



## Development
How do I do `X` in this rust project?

### Setup Environment

1. Install Rust via curl-pipe

   ```sh
   curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
   ```

2. Create a development database

    ```sh
    createdb telemetry --owner=postgres -U postgres
    ```

3. Run `kube proxy` to pretend you are running in the kube environmnet

### Workflow
Common rust commands:

 - `cargo run` – run (like a script) with debug symbols
 - `cargo build` – compile with debug symbols (for use with a debugger); outputs to `target/debug/telemetry-bot`
 - `cargo build --release` – compile optimized build for production; outputs to `target/release/telemetry-bot`
 - `cargo doc --open` – build and open API docs for this project and all of its dependencies
 - `cargo test` – run integration and unit tests
 
To reset the database:

```sh
dropdb telemetry -U postgres
createdb telemetry --owner=postgres -U postgres
cargo run -p migrate
```

### Libraries for X:
Links to online documentation for important libraries (almost always on `docs.rs/<CRATE>`). 

 - std lib: [std](https://doc.rust-lang.org/std/)
 - database client: [sqlx](https://docs.rs/sqlx)
