               ┌──────────────────────────────────────────┐
               │                 Circom                   │
               │    (A DSL for constructing ZK circuits)  │
               └──────────────────────────────────────────┘
                                  │
        ┌─────────────────────────┼─────────────────────────┐
        │                         │                         │
        ▼                         ▼                         ▼
┌────────────────┐      ┌────────────────────┐    ┌───────────────────────┐
│ Circom Language│      │ Circuit Structure  │    │   Cryptographic Base  │
└────────────────┘      └────────────────────┘    └───────────────────────┘
        │                         │                         │
        │                         │                         │
        ▼                         ▼                         ▼
┌───────────────┐       ┌──────────────────┐       ┌────────────────────┐
│ Syntax & Types│       │ Templates & Mods │       │ Field Arithmetic   │
│ - signals     │       │ - template       │       │ - prime fields     │
│ - inputs/outs │       │ - components     │       │ - mod arithmetic   │
│ - arrays      │       │ - parameters     │       │ - EC ops intro     │
└───────────────┘       └──────────────────┘       └────────────────────┘
        │                         │                         │
        ▼                         ▼                         ▼
┌───────────────┐       ┌──────────────────┐       ┌────────────────────────┐
│  Constraints  │       │  Composition     │       │  Hash & Merkle         │
│ - polynomial  │       │ - loops          │       │ - Poseidon / MiMC      │
│ - linear eqns │       │ - arrays         │       │ - Merkle tree logic    │
│ - R1CS logic  │       │ - modular design │       │ - Signature circuits   │
└───────────────┘       └──────────────────┘       └────────────────────────┘
        │                         │                         │
        └───────────────┬─────────┴───────────────┬─────────┘
                        ▼                         ▼
           ┌─────────────────────┐       ┌────────────────────────┐
           │  Circom Compiler    │       │   Standard Libraries   │
           │   (circom → R1CS)   │       │     circomlib          │
           └─────────────────────┘       └────────────────────────┘
                        │                         │
                        ▼                         ▼
       ┌──────────────────────────────────────────────────────┐
       │                 Witness Generation                   │
       │   (generate_witness.js / wasm / snarkjs witness)     │
       └──────────────────────────────────────────────────────┘
                        │
                        ▼
       ┌──────────────────────────────────────────────────────┐
       │                     R1CS System                      │
       │         (Rank-1 Constraint System matrices)          │
       │      A, B, C matrices → sparse structure → FEM       │
       └──────────────────────────────────────────────────────┘
                        │
                        ▼
       ┌──────────────────────────────────────────────────────┐
       │                Proving Pipeline                      │
       │             (via snarkjs / Groth16)                  │
       │  - setup: CRS                                        │
       │  - proving key & verification key                    │
       │  - generate proof                                    │
       │  - verify proof                                      │
       └──────────────────────────────────────────────────────┘
                        │
                        ▼
       ┌──────────────────────────────────────────────────────┐
       │              On-chain / Off-chain Integration        │
       │  - Solidity verifier                                 │
       │  - circuit inputs on-chain                           │
       │  - proof verification                                │
       └──────────────────────────────────────────────────────┘
