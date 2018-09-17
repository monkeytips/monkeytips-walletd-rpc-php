<p align="center"><a href="http://monkeytips.top" target="_blank" style="max-width:50%;"><img src="https://avatars3.githubusercontent.com/u/40376113?s=200&v=4"></a></p>

---

# Monkeytips Walletd RPC PHP

Monkeytips Walletd RPC PHP is a PHP wrapper for the monkeytips walletd JSON-RPC interface.

---

1) [Install monkeytips Walletd RPC PHP](#install-monkeytips-walletd-rpc-php)
1) [Methods](#methods)
1) [Examples](#examples)
1) [License](#license)

---



## Install Monkeytips Walletd RPC PHP

This package requires PHP >=7.1.3. Require this package with composer:

```
composer require monkeytips/monkeytips-walletd-rpc-php
```

## Methods

| Method        | Params   | Description   |
| ------------- | ------------- | ------------- |
| reset | $viewSecretKey |	reset() method allows you to re-sync your wallet. |
| save |  |	save() method allows you to save your wallet by request. |
| getViewKey |  |	getViewKey() method returns address view key. |
| getSpendKeys | $address |	getSpendKeys() method returns address spend keys. |
| getStatus |  |	getStatus() method returns information about the current RPC Wallet state: block_count, known_block_count, last_block_hash and peer_count. |
| getAddresses |  |	getAddresses() method returns an array of your RPC Wallet's addresses. |
| createAddress | $secretSpendKey, $publicSpendKey |	createAddress() method creates an address. |
| deleteAddress | $address |	deleteAddress() method deletes a specified address. |
| getBalance | $address |	getBalance() method returns a balance for a specified address. If address is not specified, returns a cumulative balance of all RPC Wallet's addresses. |
| getBlockHashes | $firstBlockIndex, $blockCount |	getBlockHashes() method returns an array of block hashes for a specified block range. |
| getTransactionHashes | $blockCount, $firstBlockIndex, $blockHash, $addresses, $paymentId |	getTransactionHashes() method returns an array of block and transaction hashes. |
| getTransactions | $blockCount, $firstBlockIndex, $blockHash, $addresses, $paymentId |	getTransactions() method returns information about the transactions in specified block range or for specified addresses. |
| getUnconfirmedTransactionHashes | $addresses |	getUnconfirmedTransactionHashes() method returns information about the current unconfirmed transaction pool or for a specified addresses. |
| getTransaction | $transactionHash |	getTransaction() method returns information about the specified transaction. |
| sendTransaction | $anonymity, $transfers, $fee, $addresses, $unlockTime, $extra, $paymentId, $changeAddress |	sendTransaction() method creates and sends a transaction. |
| createDelayedTransaction | $anonymity, $transfers, $fee, $addresses, $unlockTime, $extra, $paymentId, $changeAddress |	createDelayedTransaction() method creates but not sends a transaction. |
| getDelayedTransactionHashes |  |	getDelayedTransactionHashes() method returns hashes of delayed transactions. |
| deleteDelayedTransaction | $transactionHash |	deleteDelayedTransaction() method deletes a specified delayed transaction. |
| sendDelayedTransaction | $transactionHash |	sendDelayedTransaction() method sends a specified delayed transaction. |
| sendFusionTransaction | $threshold, $anonymity, $addresses, $destinationAddress |	sendFusionTransaction() method creates and sends a fusion transaction. |
| estimateFusion | $threshold, $addresses |	estimateFusion() method allows to estimate a number of outputs that can be optimized with fusion transactions. |
| getMnemonicSeed | $address |	getMnemonicSeed() method functions nearly the same as getSpendKeys(). It returns the mnemonic seed for the given address. |
| createIntegratedAddress | $address, $paymentId | Combines an address and a paymentId into an 'integrated' address, which contains both in an encoded form. This allows users to not have to supply a payment Id in their transfer, and hence cannot forget it. |
| getFeeInfo |  | getFeeInfo() retrieves the fee and address of the public node you are connected to, that will be applied to each transaction. |

## Examples

```php
use monkeytips\Walletd;

$walletd = new Walletd\Client();

$response = $walletd->getBalance($walletAddress);
```

```php
use monkeytips\Walletd;

$config = [
    'rpcHost'     => 'http://127.0.0.1',
    'rpcPort'     => 8070,
    'rpcPassword' => 'test',
];

$walletd = new Walletd\Client($config);

$json = $walletd->getBalance($walletAddress)->getBody()->getContents();

echo $json;

> {"id":0,"jsonrpc":"2.0","result":["availableBalance":100,"lockedAmount":50]}
```

## License

monkeytips Walletd RPC PHP is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT).
