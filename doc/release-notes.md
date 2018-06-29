(note: this is a temporary file, to be added-to by anybody, and moved to
release-notes at release time)

Susucoin Core version *version* is now available from:

  <https://susukino.com>

This is a new major version release, including new features, various bugfixes
and performance improvements, as well as updated translations.

Please report bugs using the issue tracker at GitHub:

  <https://github.com/susucoin/susucoin/issues>

How to Upgrade
==============

If you are running an older version, shut it down. Wait until it has completely
shut down (which might take a few minutes for older versions), then run the
installer (on Windows) or just copy over `/Applications/Susucoin-Qt` (on Mac)
or `susucoind`/`susucoin-qt` (on Linux).

Compatibility
==============

Susucoin Core is extensively tested on multiple operating systems using
the Linux kernel, macOS 10.8+, and Windows 7 and newer (Windows XP is not supported).

Susucoin Core should also work on most other Unix-like systems but is not
frequently tested on them.

Notable changes
===============

Bug Fixes
---------

A reindexing issue was fixed caused by the genesis block being a version 1 block.

Denial-of-Service vulnerability
-------------------------------

A denial-of-service vulnerability exploitable by miners has been discovered in
Bitcoin Core versions 0.14.0 up to 0.16.99. It is recommended to upgrade any of
the vulnerable versions as soon as possible. 

- The `createrawtransaction` RPC will now accept an array or dictionary (kept for compatibility) for the `outputs` parameter. This means the order of transaction outputs can be specified by the client.
- The `fundrawtransaction` RPC will reject the previously deprecated `reserveChangeKey` option.
- `sendmany` now shuffles outputs to improve privacy, so any previously expected behavior with regards to output ordering can no longer be relied upon.
- The new RPC `testmempoolaccept` can be used to test acceptance of a transaction to the mempool without adding it.
- JSON transaction decomposition now includes a `weight` field which provides
  the transaction's exact weight. This is included in REST /rest/tx/ and
  /rest/block/ endpoints when in json mode. This is also included in `getblock`
  (with verbosity=2), `listsinceblock`, `listtransactions`, and
  `getrawtransaction` RPC commands.
- New `fees` field introduced in `getrawmempool`, `getmempoolancestors`, `getmempooldescendants` and
   `getmempoolentry` when verbosity is set to `true` with sub-fields `ancestor`, `base`, `modified`
   and `descendant` denominated in BTC. This new field deprecates previous fee fields, such as
   `fee`, `modifiedfee`, `ancestorfee` and `descendantfee`.
- The new RPC `getzmqnotifications` returns information about active ZMQ
  notifications.

- Maximum size of data in data carrier transactions has been increased from
  `83` to `516`.

- Maximum amount of `OP_RETURN` transactions in a txout has been increased 
  from `1` to `16`.

Low-level RPC changes
---------------------

- Susucoin now relays data by default. Can be disabled using the 
  `-datacarrier` flag.

Credits
=======

Thanks to everyone who directly contributed to this release:
  - sd8
  - Ron Watkins
  - lancelink

