[[Rust]]
**make sure to add the `wasm32-unknown-unknown` target** to build wasm
```
rustup target add wasm32-unknown-unknown
```
https://www.hellorust.com/setup/wasm-target/

- `trunk` hotreloads the frontend, `cargo-leptos` hotreloads the backend
- `App.rs` entrypoint for frontend `main.rs` entrypoint for backend (axum or actix)

`#[cfg(feature="ssr")]` means render only if server side rendering (sends html and augments with wasm for interactive parts)
`#[cfg(feature="csr")]` means build only if client side rendering (like SPA)

- If you’re trying to load data by running an `async` function, either once or when some other value changes, you probably want to use `create_resource`.
- If you’re trying to occasionally run an `async` function in response to something like a user clicking a button, you probably want to use `create_action`

- The goal of defining nested routes is not primarily to avoid repeating yourself when typing out the paths in your route definitions. It is actually to tell the router to display multiple `<Route/>`s on the page at the same time, side by side.


sqlx guide https://gendevel.com/sqlx-guide/
```
sqlx database create --database-url "sqlite://db.sqlite"
```

