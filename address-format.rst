Address Format
=================================
CodeChain adopted `Bitcoin's Bech32 Specification <https://github.com/bitcoin/bips/blob/master/bip-0173.mediawiki#bech32>`_. However,
there are differences. Codechain does not have a seperator. Also, there are two types of addresses used in CodeChain, which are
Platform Address and Asset Address. Platform Addresses are used for CCC, while Asset Addresses are used
for mintable assets. These addresses have a human readable part, followed by code. Platform Addresses have a ``"ccc"`` tag, while
Asset Addresses have a ``"cca"`` tag.

Platform Account Address Format
------------------------------------
HRP: ``"ccc"`` for Mainnet, ``"tcc"`` for Testnet.

Data Part: ``version`` . ``body``

**Version 0 (0x00)**
Data body: ``Account ID`` (20 bytes)

Account ID is a result of ripemd160 of blake256 of a public key (64 bytes uncompressed form).

Asset Transfer Address Format
------------------------------------
HRP: ``"cca"`` for Mainnet, ``"tca"`` for Testnet.

Data: ``version`` . ``body``

**Version 0 (0x00)**
Data body: ``type`` . ``payload``

Type 0 (0x00)
Payload: <LockScriptHash> (32 bytes)

Type 0 with given payload represents:

Lock Script Hash: <LockScriptHash>
Parameters: []
Type 1 (0x01)
Payload: <Public Key Hash> (32 bytes)

Type 1 with given payload represents:

Lock Script Hash: P2PKH Standard Script Hash
Parameters: [<Public Key Hash>]

.. _remote key store:
