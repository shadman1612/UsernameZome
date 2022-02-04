# Zome Developer Setup

This folder has an example DNA for the `username` zome. The actual code for the zome is in `zomes/username`.

To change the code, you can work either opening VSCode inside the root folder of the repo or in this folder, you should have rust intellisense either way.

## Requirements

- Having run through [holochain RSM installation](https://github.com/holochain/holochain-dna-build-tutorial).
- Run all the steps described in this README.md inside the `nix-shell` of the `holochain` core repository.
- Have [`holochain-run-dna`](https://www.npmjs.com/package/@holochain-open-dev/holochain-run-dna) installed globally, and the `lair-keystore` described in its README as well.

## Building

```bash
   nix-shell 
   CARGO_TARGET=target cargo build --release --target wasm32-unknown-unknown
   hc dna pack username.dna.workdir/
   hc app pack happ/

```

## Testing

After having built the DNA:

```bash
   cd test
   npm install
   npm test
```

## Running

After having built the DNA:

```bash
   hc sandbox generate happ/ --run=8888
   or the smaller version:
   hc s generate happ/ -r=8888 
```

Now `holochain` will be listening at port `8888`;

Restart the command if it fails (flaky holochain start).
