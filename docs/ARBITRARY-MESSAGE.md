## Gas Consumption `ARBITRARY-MESSAGE` Bridge Mode

#### Deployment

##### Home

| Contract            | Method                 | Min     | Max     | Avg     |
| ------------------- | ---------------------- | ------- | ------- | ------- |
| EternalStorageProxy | deployment             | 288827  | 288827  | 288827  |
| BridgeValidators    | deployment             | 1113137 | 1113137 | 1113137 |
| EternalStorageProxy | upgradeTo              | 37661   | 67673   | 64944   |
| BridgeValidators    | initialize             | 205414  | 1465535 | 454811  |
| EternalStorageProxy | transferProxyOwnership | 31113   | 31113   | 31113   |
| EternalStorageProxy | deployment             | 288827  | 288827  | 288827  |
| HomeAMB             | deployment             | 3766480 | 3766480 | 3766480 |
| EternalStorageProxy | upgradeTo              | 37661   | 67673   | 64944   |
| HomeAMB             | initialize             | 237249  | 256485  | 255152  |
| EternalStorageProxy | transferProxyOwnership | 31113   | 31113   | 31113   |
| Total               |                        | 6037482 | 7376863 | 6359348 |

- Eth current price (21/02/2023):
  - slow: 23 gwei
  - average: 24 gwei
  - fast: 24 gwei
- Price:
  - min: 23 \* 6037482 = 138862086 gwei (~0,138862086 ETH)
  - max: 24 \* 7376863 = 177044712 gwei (~0,177044712 ETH)
  - average: (23 \* 6037482 + 24 \* 6037482 + 24 \* 6037482 + 7376863 \* 23 + 7376863 \* 24 + 7376863 \* 24 + 5224217 \* 23 + 5224217 \* 24 + 5224217 \* 24) / 9 = 155992467 gwei (~0,155992467 ETH)

##### Foreign

| Contract            | Method                 | Min     | Max     | Avg     |
| ------------------- | ---------------------- | ------- | ------- | ------- |
| EternalStorageProxy | deployment             | 288827  | 288827  | 288827  |
| BridgeValidators    | deployment             | 1113137 | 1113137 | 1113137 |
| EternalStorageProxy | upgradeTo              | 37661   | 67673   | 64944   |
| BridgeValidators    | initialize             | 205414  | 1465535 | 454811  |
| EternalStorageProxy | transferProxyOwnership | 31113   | 31113   | 31113   |
| EternalStorageProxy | deployment             | 288827  | 288827  | 288827  |
| ForeignAMB          | deployment             | 2630200 | 2630200 | 2630200 |
| EternalStorageProxy | upgradeTo              | 37661   | 67673   | 64944   |
| ForeignAMB          | initialize             | 256301  | 256301  | 256301  |
| EternalStorageProxy | transferProxyOwnership | 31113   | 31113   | 31113   |
| Total               |                        | 4920254 | 6240399 | 5224217 |

- Price:
  - min: 23 \* 4920254 = 113165842 gwei (~0,113165842 ETH)
  - max: 24 \* 6240399 = 149769576 gwei (~0,149769576 ETH)
  - average: (23 \* 4920254 + 24 \* 4920254 + 24 \* 4920254 + 6240399 \* 23 + 6240399 \* 24 + 6240399 \* 24 + 6359348 \* 23 + 6359348 \* 24 + 6359348 \* 24) / 9 = 138213341.222 gwei (~0,138213341222 ETH)

#### Usage

##### Validators

| Contract                                                         | Method             | Min    | Max     | Avg    |
| ---------------------------------------------------------------- | ------------------ | ------ | ------- | ------ |
| To sign at the Home (each validator)                             |
| HomeAMB                                                          | submitSignature    | 156870 | 277671  | 237493 |
| To relay signatures from the Home to the Foreign (one validator) |
| ForeignAMB                                                       | executeSignatures  | 139479 | 1397163 | 314691 |
| To sign and relay from the Foreign to the Home (each validator)  |
| HomeAMB                                                          | executeAffirmation | 65514  | 238169  | 182426 |

#### Test on Goerli & G.U.Sandbox

- Network gas price:
  - Sepolia: 1 Gwei
  - G.U.Sandbox: 10 Gwei
- Balance before:
  - Sepolia: 1.179
  - G.U.Sandbox: 8.2883
- Balance after:
  - Sepolia: 1.1739 (gasUsed: 5100000)
  - G.U.Sandbox: 8.227 (gasUsed: 6130000)
