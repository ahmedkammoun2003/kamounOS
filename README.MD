# KamounOS

KamounOS is a custom operating system kernel written in Rust. It's designed to be a minimal, educational operating system that demonstrates various OS concepts and Rust's capabilities in systems programming.

## Features

- Bare-metal x86_64 support
- Custom bootloader integration
- Interrupt handling
- Memory management with paging
- Heap allocation
- Asynchronous task execution
- Keyboard input handling
- VGA text mode output

## Prerequisites

- Rust nightly toolchain
- QEMU (for running the OS)
- `bootimage` tool

## Building

1. Install the Rust nightly toolchain:
   ```rust
   rustup override set nightly
   ```

2. Install the `bootimage` tool:
   ```rust
   cargo install bootimage
   ```

3. Build the project:
   ```rust
   cargo build
   ```

## Running

To run KamounOS in QEMU:

```
cargo run
```
binary file inside the `target/x86_64-kamounos/debug/` directory

## Testing

KamounOS includes a custom test framework. To run the tests:

```
cargo test
```

## Project Structure

- `src/`: Contains the main kernel code
- `tests/`: Integration tests
- `Cargo.toml`: Project dependencies and configuration
- `.cargo/config.toml`: Cargo configuration for custom target

## Key Components

- `main.rs`: Kernel entry point
- `vga_buffer.rs`: VGA text mode driver
- `interrupts.rs`: Interrupt handling
- `memory.rs`: Memory management
- `allocator/`: Heap allocation implementations
- `task/`: Task management
- `keyboard.rs`: Keyboard input handling
- `gdt.rs`: Global Descriptor Table setup
- `idt.rs`: Interrupt Descriptor Table setup
- `linker.rs`: Linker script for the kernel
- `boot.rs`: Bootloader integration

## Testing

```
cargo test
```

### Available Tests

1. **Basic Functionality Tests**
   - `test_println_simple`: Verifies basic println functionality
   - `test_println_many`: Tests multiple println calls
   - `test_println_output`: Checks the actual output of println

2. **Interrupt Handling Tests**
   - `test_breakpoint_exception`: Ensures breakpoint exceptions are handled correctly

3. **Heap Allocation Tests**
   - `simple_allocation`: Tests basic heap allocation
   - `large_vec`: Verifies allocation of a large vector
   - `many_boxes`: Checks multiple small allocations
   - `many_boxes_long_lived`: Tests long-lived allocations alongside short-lived ones

4. **Stack Overflow Test**
   - Located in `tests/stack_overflow.rs`: Verifies proper handling of stack overflows

5. **Should Panic Test**
   - Located in `tests/should_panic.rs`: Ensures that certain operations cause a panic as expected

### Running Specific Tests

To run a specific test, use:

```
cargo test <test_name>
```

For example:

```
cargo test test_println_simple
```

### Adding New Tests

- For unit tests, add functions with the `#[test_case]` attribute in the relevant source files.
- For integration tests, create new files in the `tests/` directory.