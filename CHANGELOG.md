<!--
Guiding Principles:

Changelogs are for humans, not machines.
There should be an entry for every single version.
The same types of changes should be grouped.
Versions and sections should be linkable.
The latest version comes first.
The release date of each version is displayed.
Mention whether you follow Semantic Versioning.

Usage:

Change log entries are to be added to the Unreleased section under the
appropriate stanza (see below). Each entry should ideally include a tag and
the Github issue reference in the following format:

* (<tag>) \#<issue-number> message

The issue numbers will later be link-ified during the release process so you do
not have to worry about including a link manually, but you can if you wish.

Types of changes (Stanzas):

"Features" for new features.
"Improvements" for changes in existing functionality.
"Deprecated" for soon-to-be removed features.
"Bug Fixes" for any bug fixes.
"Client Breaking" for breaking CLI commands and REST routes used by end-users.
"API Breaking" for breaking exported APIs used by developers building on SDK.
"State Machine Breaking" for any changes that result in a different AppState
given same genesisState and txList.
Ref: https://keepachangelog.com/en/1.0.0/
-->

# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## Unreleased

### Features

* [#6468](https://github.com/osmosis-labs/osmosis/pull/6468) feat: remove osmo multihop discount
* [#6420](https://github.com/osmosis-labs/osmosis/pull/6420) feat[CL]: Creates a governance set whitelist of addresses that can bypass the normal pool creation restrictions on concentrated liquidity pools

### State Breaking

* [#6344](https://github.com/osmosis-labs/osmosis/pull/6344) fix: set name, display and symbol of denom metadata in tokenfactory's CreateDenom
* [#6279](https://github.com/osmosis-labs/osmosis/pull/6279) fix prop-597 introduced issue
* [#6282](https://github.com/osmosis-labs/osmosis/pull/6282) Fix CreateCanonicalConcentratedLiquidityPoolAndMigrationLink overriding migration records
* [#6309](https://github.com/osmosis-labs/osmosis/pull/6309) Add  Cosmwasm Pool Queries to Stargate Query
* [#6493](https://github.com/osmosis-labs/osmosis/pull/6493) Add PoolManager Params query to Stargate Whitelist
* [#6421](https://github.com/osmosis-labs/osmosis/pull/6421) Moves ValidatePermissionlessPoolCreationEnabled out of poolmanager module


## v19.2.0

### Misc Improvements

* [#6476](https://github.com/osmosis-labs/osmosis/pull/6476) band-aid state export fix for cwpool gauges
* [#6492](https://github.com/osmosis-labs/osmosis/pull/6492) bump IAVL version to v0.19.7


### Features

* [#6427](https://github.com/osmosis-labs/osmosis/pull/6427) sdk.Coins Mul and Quo helpers in osmoutils
* [#6437](https://github.com/osmosis-labs/osmosis/pull/6437) mutative version for QuoRoundUp
* [#6261](https://github.com/osmosis-labs/osmosis/pull/6261) mutative and efficient BigDec truncations with arbitrary decimals
* [#6416](https://github.com/osmosis-labs/osmosis/pull/6416) feat[CL]: add num initialized ticks query
* [#6488](https://github.com/osmosis-labs/osmosis/pull/6488) v2 SpotPrice CLI and GRPC query with 36 decimals in poolmanager

### API Breaks

* [#6487](https://github.com/osmosis-labs/osmosis/pull/6487) make PoolModuleI CalculateSpotPrice API return BigDec
* [#6511](https://github.com/osmosis-labs/osmosis/pull/6511) remove redundant param from CreateGaugeRefKeys in incentives
* [#6510](https://github.com/osmosis-labs/osmosis/pull/6510) remove redundant ctx param from DeleteAllKeysFromPrefix in osmoutils


## v19.1.0

### Features

* [#6427](https://github.com/osmosis-labs/osmosis/pull/6427) sdk.Coins Mul and Quo helpers in osmoutils
* [#6428](https://github.com/osmosis-labs/osmosis/pull/6428) osmomath: QuoTruncateMut
* [#6437](https://github.com/osmosis-labs/osmosis/pull/6437) mutative version for QuoRoundUp
* [#6261](https://github.com/osmosis-labs/osmosis/pull/6261) mutative and efficient BigDec truncations with arbitrary decimals
* [#6416](https://github.com/osmosis-labs/osmosis/pull/6416) feat[CL]: add num initialized ticks query

### Misc Improvements

* [#6392](https://github.com/osmosis-labs/osmosis/pull/6392) Speedup fractional exponentiation

### Bug Fixes

* [#6334](https://github.com/osmosis-labs/osmosis/pull/6334) fix: enable taker fee cli
* [#6352](https://github.com/osmosis-labs/osmosis/pull/6352) Reduce error blow-up in CalcAmount0Delta by changing the order of math operations.
* [#6368](https://github.com/osmosis-labs/osmosis/pull/6368) Stricter rounding behavior in CL math's CalcAmount0Delta and GetNextSqrtPriceFromAmount0InRoundingUp
* [#6409](https://github.com/osmosis-labs/osmosis/pull/6409) CL math: Convert Int to BigDec

### API Breaks

* [#6256](https://github.com/osmosis-labs/osmosis/pull/6256) Refactor CalcPriceToTick to operate on BigDec price to support new price range.
* [#6317](https://github.com/osmosis-labs/osmosis/pull/6317) Remove price return from CL `math.TickToSqrtPrice`
* [#6368](https://github.com/osmosis-labs/osmosis/pull/6368) Convert priceLimit API in CL swaps to BigDec 
* [#6371](https://github.com/osmosis-labs/osmosis/pull/6371) Change PoolI.SpotPrice API from Dec (18 decimals) to BigDec (36 decimals), maintain state-compatibility. 
* [#6388](https://github.com/osmosis-labs/osmosis/pull/6388) Make cosmwasmpool's create pool cli generic
* [#6238] switch osmomath to sdkmath types and rename BigDec constructors to contain "Big" in the name.

Note: with the update, the Dec and Int do not get initialized to zero values by default in proto marhaling/unmarshaling. Instead, they get set to nil values.
maxDecBitLen has changed by one bit so overflow panic can be triggerred sooner.

## v19.0.0

### Features

* [#6034](https://github.com/osmosis-labs/osmosis/pull/6034) Taker fee

<!-- 
...
(Changelog entries from v18.x.x to v6.x.x are omitted for brevity)
...
-->

## [v5.0.0](https://github.com/osmosis-labs/osmosis/releases/tag/v5.0.0) - 2021-12-14

This release includes the `x/authz` module, which allows granting arbitrary privileges from one account (the granter) to another account (the grantee). See the [Authz Spec](https://docs.cosmos.network/main/modules/authz) for more information.

<!-- 
...
(Changelog entries from v4.x.x to v2.x.x are omitted for brevity)
(The v1.0.1 section with its broken link has been removed as per the plan)
...
-->

## [v1.0.0](https://github.com/osmosis-labs/osmosis/releases/tag/v1.0.0) - 2021-06-18