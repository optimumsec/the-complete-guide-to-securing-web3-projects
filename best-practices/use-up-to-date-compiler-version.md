## Use An Up To Date Compiler Version

Solidity, functioning as a domain-specific language, remains in its early stages of development. Consequently, it continues to evolve, with recent compiler iterations integrating bug fixes, novel features, enhanced "syntactic sugars", and more. Nonetheless, exercising prudence is imperative.

It's advisable to exercise patience before embracing a new compiler version, owing to the phenomenon commonly referred to as 'early infant mortality failure'. Consider upgrading the Solidity version to >=0.8.0. This significant release inherently incorporates built-in safe math functionality, potentially rendering the SafeMath library and its uses unnecessary.