# Chapter 1 - Environement Setup

## Rust Installation

Veloren is made in Rust so you need the lastest version of Rust installed. 
To install Rust please refer to the official [Rust website](https://www.rust-lang.org/tools/install).

If you are on windows check if the linker as been correctly installed or you WILL NOT able to compile your plugin.

## IDEs

You can use the IDE of your choice even through we recomend [VSCode](https://code.visualstudio.com/) with the [rust-analyzer](https://marketplace.visualstudio.com/items?itemName=matklad.rust-analyzer) extension.
[CLion](https://www.jetbrains.com/clion/) or other [Intelij based IDEs](https://www.jetbrains.com/idea/) are also a good choice with the official [Jetbrain Rust plugin](https://www.jetbrains.com/rust/). 

## Basic setup

We recommend cloning the [Veloren Plugin Template Repo](https://github.com/ccgauche/veloren_plugin_template).

You can also create a rust project in library mode:
```
cargo new my_plugin --lib
```

Then add to your `Cargo.toml`:
```
[lib]
crate-type = ["cdylib"]
```

## Plugin configuration

The plugin should be place along a configuration file in a TAR archive named `plugin.toml`

Which should follow this format
```toml
name = "veloren_plugin_template"
modules = ["veloren_plugin_template.wasm"]
dependencies = []
target = "BOTH"
```

You can have multiple WASM modules in one plugin by adding more members to `modules`.

`target` isn't implemented yet but will be usefull when network sharing is added.


## Build the plugin

To build the plugin then use:
```
cargo build --release --target=wasm32-unknown-unknown
```

Then create a TAR archive with the `veloren_plugin_template.wasm` file located in `target/wasm32-unknown-unknown/release` and the `plugin.toml` and place it into the  `assets/plugin` folder of your game, if the folder doesn't exist create it.
**Note: the name of the tar file should end by `.plugin.tar`**

