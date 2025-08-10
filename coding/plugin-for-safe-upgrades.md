## Use a Plugin for Safe Upgrades

When setting up a proxy for a contract, there are specific restrictions concerning the contract's code. Notably, the contract mustn't include a constructor, and it's advised to steer clear of utilizing operations like selfdestruct or delegatecall due to security considerations.

In addition, storage variables in the proxy can potentially be overwritten when deploying new versions of the implementation contract. This happens because the storage layout of the proxy and implementation must remain consistent across upgrades. Any mismatch in storage variable declarations or order can result in overwritten or corrupted data, leading to unpredictable behavior.

It is highly recommended to use a [plugin](https://docs.openzeppelin.com/upgrades-plugins/1.x/) that ensures the newly introduced contract complies with the safe upgrades rules.