---
layout: default
---

<img src="kusacoin.png" width="128" height="128">

## Download

<dl>
  <dt>Windows/Mac</dt>
  <dd><a href="https://github.com/kusacoin/kusacoin/releases">https://github.com/kusacoin/kusacoin/releases</a></dd>
  <dt>Linux</dt>
  <dd><a href="https://github.com/kusacoin/kusacoin/blob/master/doc/build-unix.md">https://github.com/kusacoin/kusacoin/blob/master/doc/build-unix.md</a></dd>
</dl>

## Features

- Some opcodes are re-enabled
  - `OP_CAT`, `OP_SUBSTR`, `OP_LEFT`, `OP_RIGHT`, `OP_INVERT`, `OP_AND`, `OP_OR`, `OP_XOR`, `OP_2MUL`, `OP_2DIV`, `OP_MUL`, `OP_DIV`, `OP_MOD`, `OP_LSHIFT`, `OP_RSHIFT`
- [Non-standard](https://bitcoin.org/en/glossary/standard-transaction) transactions are acceptable
- `poolrawtransaction` command is implemented
  - `poolrawtransaction` adds a transaction into mempool, but not send to network
  - You can mine a block containing the transaction by yourself

## Specifications

<dl>
  <dt>Currency unit</dt>
  <dd>KUSA</dd>
  <dt>PoW algorithm</dt>
  <dd>Lyra2REv2</dd>
  <dt>Difficulty adjustment algorithm</dt>
  <dd><a href="https://github.com/zawy12/difficulty-algorithms/issues/3">Linearly Weighted Moving Average</a></dd>
  <dt>Default port</dt>
  <dd>9393</dd>
  <dt>Default RPC port</dt>
  <dd>9392</dd>
  <dt>Others</dt>
  <dd>Same as original Bitcoin</dd>
</dl>

## Mining

You can mine any miner which support Lyra2REv2.
Supporting segwit is recommended.
Cpuminer is [here](https://github.com/kusacoin/cpuminer).

[This script](https://github.com/kusacoin/kusacoin2bitcoin/blob/master/address.py) convert **Non-bech32** Kusacoin address into Bitcoin address format.

### example

```shell-session
$ ./kusacoin-qt --server --rpcuser=name --rpcpassword=password
$ python address.py VzmRA4H83cPRffPZiTKXe5KjWSKFyLoLgZq71i
3GEEveDgMNvyFcnFMq34nsTYo5Rt7Ud2e3
$ ./minerd -a lyra2rev2 -o localhost:9392 -O name:password --coinbase-addr=3GEEveDgMNvyFcnFMq34nsTYo5Rt7Ud2e3 --no-longpoll --no-getwork
```
