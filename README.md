# Hutter Prize / enwik9 — experimental compact-footer candidate

Project contact: **Filip Majchrzak**. Derived from **Marcus Wölk's GPL-3.0 cmix-neif 2.0**, with credit retained for the original authors and contributors.

> **Research release; not a verified Hutter Prize record.** The modified pair has not passed a complete end-to-end 1,000,000,000-byte decompression and fresh recompression. The upstream runtime and RAM figures are not measurements of this modified pair.

## Download — [v0.1.0-experimental](https://github.com/kosza123/hutter-prize-filip-majchrzak/releases/tag/v0.1.0-experimental)

- [archive9 — Linux x86-64 self-extracting executable](https://github.com/kosza123/hutter-prize-filip-majchrzak/releases/download/v0.1.0-experimental/archive9) — **89,346,233 bytes**
- [comp9 — Linux x86-64 compressor](https://github.com/kosza123/hutter-prize-filip-majchrzak/releases/download/v0.1.0-experimental/comp9) — **4,042,419 bytes**
- [Complete patched source and build scripts (ZIP)](https://github.com/kosza123/hutter-prize-filip-majchrzak/releases/download/v0.1.0-experimental/compact-neif2-source.zip)
- [Exact patch](https://github.com/kosza123/hutter-prize-filip-majchrzak/releases/download/v0.1.0-experimental/compact_neif2.patch)
- [Technical documentation and verification limits](https://github.com/kosza123/hutter-prize-filip-majchrzak/releases/download/v0.1.0-experimental/TECHNICAL_README.md)

The **combined competition size S = 93,388,652 bytes**, 304 bytes smaller than the original `cmix-neif-2.0` entry (S = 93,388,956 bytes).

## SHA-256

```text
65715aaa39f774e7a1e3267b2691f942f1f1c412a33b61e722dbaa82afaa16d8  archive9
b883579ced9c194eff04e4a62e3aabd0e5ee5a65a91f0de2afa8719db80f13a3  comp9
159b85351e5f76e60cbe32e04c677847a9ecba3adc79addab6f4c6c7aa3744bc  enwik9 (canonical expected output)
```

## Usage (Linux x86-64)

```bash
chmod +x archive9 comp9
./archive9
```

A complete run should create `enwik9_uncompressed` from the self-extracting archive. To compress, put `enwik9` in the current directory and invoke `./comp9`.

## What has been tested

- Exact file sizes and SHA-256 of the published binaries.
- The decoder started and reached **0.10%** of its work during a **95-second** test before deliberate timeout.
- Its embedded coded stream and model-weight container matched their upstream reference hashes.

**Not done:** complete 1 GB lossless verification of the modified `archive9`, full `comp9` recompression, and formal time/RAM/disk measurements of the modified pair. This package's archive was assembled from the upstream reference encoded data and weights.

The sole 304-byte reduction would not meet the prize's minimum 1% reduction if Marcus Wölk's preceding entry is accepted as the prior record.

## Attribution and license

- Upstream project: [marwoelk/cmix-neif-2.0](https://github.com/marwoelk/cmix-neif-2.0).
- Upstream commit: `35d1957a5074db802fc134126afc77b76d931761`.
- License: GPL-3.0, including third-party notices in the source package.
- The model, weights, and original coding algorithm are upstream contributions. Filip Majchrzak is credited as project contact for the experimental compact-footer variant.

See [official Hutter Prize rules](https://hutter1.net/prize/hrules.htm) for eligibility, verification, authorship and prize-division requirements.
