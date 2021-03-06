# Test

## Unit Tests

To run unit test of the blockchain node:

```
cargo test
```

(WIP: run pRuntime unit tests)

## Coverage

A source-based code coverage can be generated by [grcov](https://github.com/mozilla/grcov). We have prepared a convenient script to run it for our pallets:

```bash
./scripts/coverage-pallets.sh
```

The script generates a HTML report. It's known to always generate some false negative.

## End-to-end Tests

Phala has an end-to-end (E2E) test suite that runs all the core components (node, relayer, and pRuntime). To run the E2E test, please prepare first:

1. Build the blockchain and relayer (pherrry):

    ```bash
    cargo build --release
    ```

2. Build pRuntime:

    ```bash
    cd standalone/pruntimes
    SGX_MODE=SW make
    ```

3. Initialize the E2E test project (Make sure you have node.js >=14 and yarn installed):

    ```bash
    cd e2e
    yarn
    yarn build:proto
    ```

The preparation is only required once. If you changed the code, you just need to rebuild the parts you have changed. Now run the E2E test:

```bash
yarn test
```
