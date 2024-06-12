# The Nexus zkVM

The Nexus zkVM is a modular, extensible, open-source, and highly-parallelized zkVM, designed to run at *a trillion CPU cycles proved per second* given enough machine power.

## 1. Fork the Official Repo - https://github.com/nexus-xyz/nexus-zkvm 
## 2. Login with Gitpod.io

## 3. Press CNTRL+C

## 4. Install Cmake

```
sudo apt install cmake
```
## 5. Install Build Essential 
```
sudo apt update
sudo apt install build-essential
```


### 6. Install Rust

```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

```
### 7. Input 1 and proceed 

```
. "$HOME/.cargo/env"
```

### 8. With the RISC-V target:

```shell
rustup target add riscv32i-unknown-none-elf
```

### 9. Then install the Nexus zkVM:

```shell
cargo install --git https://github.com/nexus-xyz/nexus-zkvm nexus-tools --tag 'v1.0.0'
```

### 10. Create a new Nexus project

```shell
cargo nexus new nexus-project
```

This will create a new Rust project directory with the following structure:

```shell
./nexus-project
├── Cargo.lock
├── Cargo.toml
└── src
    └── main.rs
```

### 11. Move to Directory, Replace the code and press CNTL+X, Y, Enter

```
cd nexus-project
cd src
nano main.rs
```
As an example, you can change the content of `./src/main.rs` to:

```rust
#![no_std]
#![no_main]

fn fib(n: u32) -> u32 {
    match n {
        0 => 0,
        1 => 1,
        _ => fib(n - 1) + fib(n - 2),
    }
}

#[nexus_rt::main]
fn main() {
    let n = 7;
    let result = fib(n);
    assert_eq!(result, 13);
}
```


### 12. Run your program

```bash
cargo nexus run
```

This command should run successfully. To print the full step-by-step execution trace on the NVM, run:

```bash
cargo nexus run -v
```

### 4. Prove your program

Generate a proof for your Rust program using the Nexus zkVM.

```shell
cargo nexus prove
```

This command will save the proof to `./nexus-proof`.

### 5. Verify your proof

Finally, load and verify the proof:

```shell
cargo nexus verify
```



SAVE ```NEXUS-PROOF``` SOMEWHERE IN DIRECTORY

![image](https://github.com/mztacat/nexus-zkvm/assets/31314340/c66f422d-ce36-4580-98a0-9e2540e4de41)

