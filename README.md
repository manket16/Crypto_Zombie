# Solidity Crypto Zombie (Learning Project)

This repository is a beginner-friendly Solidity project based on the CryptoZombies tutorial.  
It is organized as a chain of smart contracts where each contract adds new game features.

## Project structure

### `zombiefactory.sol` (core)
The base contract where zombies are created and stored.

- Defines the `Zombie` struct (`name`, `dna`)
- Stores all zombies in an array
- Tracks ownership with mappings
- Creates zombies with `_createZombie`
- Generates pseudo-random DNA with `_generateRandomDna`
- Lets each address create one starter zombie with `createRandomZombie`

### `zombiefeeding.sol` (feeding/breeding)
Extends `ZombieFactory` and adds DNA mixing logic.

- Adds a `KittyInterface` for CryptoKitties
- Reads kitty genes from the CryptoKitties contract
- Combines zombie DNA and target DNA via `feedAndMultiply`
- Adds `feedOnKitty` as a convenience function

### `zombiehelper.sol` (utility functions)
Extends `ZombieFeeding` and adds user-facing helper actions.

- Adds `aboveLevel` modifier for level-gated actions
- Allows changing a zombie name (`changeName`) at level 2+
- Allows changing zombie DNA (`changeDna`) at level 20+
- Intends to return all zombie IDs owned by an address (`getZombiesByOwner`)

> Note: this file appears to be from a later tutorial stage and may need additional fields (like `level`) in the `Zombie` struct to compile cleanly.

### `ownable.sol` (authorization utility)
A reusable ownership contract.

- Stores contract owner
- Exposes `onlyOwner` modifier
- Supports ownership transfer and renounce

Currently, the zombie contracts do not inherit from `Ownable` yet.

## Suggested beginner reading order

1. `zombiefactory.sol`
2. `zombiefeeding.sol`
3. `zombiehelper.sol`
4. `ownable.sol`

This order follows how features are layered through inheritance.
