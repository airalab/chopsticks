## Install

Make sure you have setup Rust environment (>= 1.64).

- Clone repository with submodules ([smoldot](https://github.com/paritytech/smoldot))
  - `git clone --recurse-submodules https://github.com/airalab/chopsticks.git && cd chopsticks`
- Move to `robonomics` branch
  - `git checkout robonomics`
- Install deps
  - `yarn`
- Build project. Please do not use IDE's built-in tools to build wasm.
  - `yarn build`

We are using the custom consensus temporarily, so need to comment one line in installed Enum.js that causing error with Robonomics consensus. Open file `./node_modules/@polkadot/types-codec/base/Enum.js` and comment line 173:
```
172 if (self.type !== keys[i]) {
173 //  throw new Error(`Cannot convert '${self.type}' via ${k}`);
174 }
175 return self.value;
```

## Run
- Robonomics in Kusama
  - `node packages/chopsticks/dist/esm/cli.js -c ./configs/robonomics-kusama.yml`

- Robonomics in Polkadot
  - `node packages/chopsticks/dist/esm/cli.js -c ./configs/robonomics-polkadot.yml`
