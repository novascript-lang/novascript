# `NovaScript`

A TypeScript-inspired systems language with real runtime types, compiled to WebAssembly and native with a Rust compiler and Zig runtime.

---

## Overview

`NovaScript` is a modern programming language designed to combine the **developer ergonomics of TypeScript** with the **performance and safety of systems languages**.

It introduces **real runtime types**, **predictable memory behavior**, and a **WASM-first execution model**, while maintaining familiar syntax for developers coming from the JavaScript and TypeScript ecosystem.

`NovaScript` aims to become a **typed systems layer for the web ecosystem**, enabling high-performance applications while simplifying the tooling and runtime complexity that currently exists in modern JavaScript environments.

---

## Why `NovaScript` Exists

Modern web development relies heavily on TypeScript and JavaScript, but the ecosystem has several structural limitations.

### Problems in the Current Ecosystem

* TypeScript types **do not exist at runtime**
* JavaScript semantics allow **dynamic mutation and unpredictable behavior**
* Tooling is fragmented across many independent tools
* Performance can be constrained by dynamic runtime execution
* Web applications increasingly need **systems-level performance**

### Goals of `NovaScript`

`NovaScript` is designed to address these issues by providing:

* **Real runtime types**
* **Predictable compilation and execution**
* **Strong static typing**
* **High-performance execution via WebAssembly**
* **A unified development toolchain**

---

## Key Features

`NovaScript` introduces several design principles that differentiate it from existing languages.

* TypeScript-inspired syntax
* Runtime-visible types with deterministic layout
* Struct-first object model
* WebAssembly-first compilation
* Optional native compilation targets
* Hybrid memory model with optional garbage collection
* Rust-based compiler architecture
* Zig-based runtime
* Integrated CLI tooling
* Simplified dependency and packaging model

---

## Example

Below is a simple example showing the core syntax of `NovaScript`.

```ts
struct User {
  id: u64
  name: string
}

fn greet(user: User): string {
  return "Hello " + user.name
}

fn main() {
  let user = User {
    id: 1,
    name: "Alice"
  }

  print(greet(user))
}
```

`NovaScript` also supports asynchronous programming.

```ts
async fn fetchUser(id: u64): User {
  return await http.get("/user/" + id)
}
```

---

## Architecture

`NovaScript` is implemented as a layered system combining several technologies.

```
NovaScript Source
        │
        ▼
Rust Compiler
(parsing, type system, code generation)
        │
        ▼
Typed Intermediate Representation
        │
        ▼
WASM / Native Code
        │
        ▼
Zig Runtime
(system interfaces and scheduler)
        │
        ▼
Bun Ecosystem Bridge
```

### Implementation Stack

* Compiler implemented in Rust
* Runtime implemented in Zig
* Primary execution target: WebAssembly
* Optional native compilation for high-performance workloads

---

## Object Model

`NovaScript` uses a **hybrid struct-first object model**.

### Structs

Structs are the primary data structure and provide deterministic memory layout.

```ts
struct Point {
  x: f64
  y: f64
}
```

### Dynamic Objects

Dynamic objects exist for flexible data such as configuration or JSON-like structures.

```ts
object config = {
  port: 3000,
  host: "localhost"
}
```

---

## Memory Model

`NovaScript` uses a **hybrid memory system**.

Default behavior uses managed memory suitable for most applications.

Advanced programs may use explicit allocation strategies.

Example:

```ts
let users = arena.alloc<User>(100)
```

This approach allows both **developer simplicity** and **systems-level performance**.

---

## Concurrency Model

`NovaScript` combines asynchronous programming with a lightweight task scheduler.

```ts
async fn fetchData() {
  return await http.get("/data")
}

task processData() {
  heavyComputation()
}
```

Parallel tasks can execute using the runtime scheduler.

---

## CLI

The `NovaScript` toolchain is accessed through a single command.

```
ns dev
ns build
ns build --release
ns test
ns fmt
ns lint
```

This unified CLI replaces the fragmented tooling commonly required in JavaScript ecosystems.

---

## Project Structure

A typical `NovaScript` project may look like the following.

```
ns.toml
src/
tests/
```

The `ns.toml` file defines package metadata and dependencies.

---

## Documentation

The full language specification is located in the `docs/spec` directory.

Specification sections include:

* Language overview
* Type system
* Modules and imports
* Memory model
* Concurrency model
* Runtime behavior
* Compilation targets
* Standard library

---

## Roadmap

The early roadmap for `NovaScript` includes the following milestones.

```
v0.1  Language specification draft
v0.2  Compiler prototype
v0.3  Runtime prototype
v0.4  WebAssembly execution
v1.0  Stable release
```

---

## Contributing

Contributions to `NovaScript` are welcome.

Please read `CONTRIBUTING.md` before submitting pull requests or issues.

Community discussions and feedback are encouraged as the language evolves.

---

## License

`NovaScript` is licensed under the MIT OR Apache-2.0 license.

See `LICENSE` for details.
