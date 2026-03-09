# Assignment 2: Keys, Addresses and Wallets

## 1. Generated Addresses
### Legacy Address (P2PKH)
- **Address:** mzs5DnhQNpN3UxRgYiNjgGYiJYmJkN3BGR
- **HD Key Path:** m/44h/1h/0h/0/0
- **Public Key:** 03534fa0f5ddab3ecd6bd9a8db504c1d67c893056dfbb6bec50244a1076253481f
- **Script Type:** P2PKH (Pay to Public Key Hash)
- **Witness:** No
### Bech32 Address (P2WPKH)
- **Address:** bcrt1qk3me9ppe7nwpec9zc9m5le65farnsrm5dny3wl
- **HD Key Path:** m/84h/1h/0h/0/2
- **Public Key:** 0230a0a1358a15cfbbb1c5aa59bfa6e42970bc5db3cb2ecffd671c5f1562d5084b
- **Script Type:** P2WPKH (Pay to Witness Public Key Hash)
- **Witness Version:** 0
### Bech32m Address (P2TR)
- **Address:** bcrt1pjgprlghtv52rsvmgwvspl4ka6y8z4zpxh8g87fxk3lf39dfu04ps8ju6h0
- **HD Key Path:** m/86h/1h/0h/0/0
- **Script Type:** P2TR (Pay to Taproot)
- **Witness Version:** 1
- 
## 2. Hardened vs Non-Hardened Keys
### Non-Hardened Keys
Non-hardened keys allow child public keys to be derived from a parent
public key without needing the private key. This is useful for watch-only
wallets. However, if a child private key is exposed, an attacker can
derive the parent private key and all sibling keys.
- Denoted without h in the path e.g. m/44/0/0
### Hardened Keys
Hardened keys require the parent private key to derive child keys.
This means even if a child private key is compromised, the parent
and sibling keys remain safe. This provides stronger security isolation.
- Denoted with h in the path e.g. m/44h/0h/0h
### Key Difference
Hardened keys sacrifice the ability to derive child public keys from
parent public keys, in exchange for better security. Most wallet
standards (BIP44, BIP84, BIP86) use hardened derivation for account
levels to protect the master key.

## 3. Deterministic vs Non-Deterministic Wallets
### Non-Deterministic Wallets
Non-deterministic wallets generate each private key randomly and
independently. Each key has no relationship to any other key. This
means every key must be backed up individually. If a backup is lost,
any keys not included are permanently lost.
### Deterministic Wallets (HD Wallets)
Deterministic wallets generate all keys from a single master seed
using a tree structure (BIP32). All keys can be recovered from just
one seed phrase (12 or 24 words).
### Why Wallet Developers Should Prefer Deterministic Wallets
1. **Single backup** - Only the seed phrase needs to be backed up
2. **Key recovery** - All keys can be restored from one seed
3. **Organization** - Keys are structured in a tree (accounts, chains)
4. **Watch-only wallets** - Public keys can be shared without exposing private keys
5. **Interoperability** - Standards like BIP44/84/86 ensure compatibility across wallets
6. **Scalability** - Unlimited keys can be generated from one seed
