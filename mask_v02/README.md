# Hutter Prize — optimized MASK / experimental source v0.2

Project contact: Filip Majchrzak. Upstream: Marcus Wölk / contributors, `cmix-neif-2.0` commit `35d1957a5074db802fc134126afc77b76d931761` (GPL-3.0). The initial compact-footer release and original upstream author credits remain unchanged.

**Status: source/build candidate, not a contest submission.** This branch does not contain a complete MASK-generated 1,000,000,000-byte `archive9`. The existing public `archive9` and `comp9` from v0.1.0-experimental use the old probability model and MUST NOT be substituted or combined with this MASK build. The full contest score `S = len(comp9)+len(archive9)` for MASK is unknown.

## What is changed

After applying the previous `compact-neif2-source.zip` release, apply `mask_v02/optimized_mask.patch`. It changes `src/predictor.cpp`, `src/predictor.h`, and `makefile` to turn on `HUTTER_RECORD_FAST_VOTE=1`, `HUTTER_RECORD_DEPTH_MASK=1` and place an early depth filter before `RecordFastVote`. The filter applies only to bit-depths 2, 6 and 7, with the same conditional expert share 0.16 as in laboratory runs. The validated lab branch used a 10 KiB sigmoidal table. No BAYES posterior update is enabled.

This patch is applied *after* the compact-footer patch, and is not a patch directly against the untouched upstream repository. The GitHub Actions workflow downloads the pinned source release and applies this patch automatically before rebuilding.

## Evidence and limits

- Independent GitHub Actions lab comparison, 2026-11-19, on a fresh 262,144 byte `enwik9` slice starting at offset 84,541,141: upstream lab `archive=42,384 B`, MASK `41,783 B`, early-depth MASK `41,783 B`. The code packing comparator is the *raw CMIX code stream*, not a full `comp9`.
- Three laboratory roundtrips: PASS byte-for-byte, SHA-256; optimized MASK total lab `255,462+41,783=297,245 B`, upstream `255,260+42,384=297,644 B`. Laboratory time and RAM were captured separately.
- These measurements do **not** establish competition legality, 1% gain on `enwik9`, or full-run time. The source pipeline uses Clang 18/PGO and the compressed program size may differ materially.

Full `enwik9` compression with the exact new binary, creation of the matching self-extracting `archive9`, and full lossless verification remain outstanding. Do not submit this code as a measured record until actual contest files exist.

## Build

Refer to `.github/workflows/build-mask-comp9.yml` for the controlled source checksum, exact patch, compiler installation, and source-only build of a candidate `comp9` (without a full `enwik9` run). The workflow's artifact is a new `comp9` only, not a replacement for the v0.1.0-experimental pair. On Ubuntu 24.04 with the release source in a directory, `git apply optimized_mask.patch`, then `bash install.sh`, then `bash build.sh` from a writable output directory.
