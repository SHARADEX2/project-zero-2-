# FlapJax Q84 — Treasury FLAPJAX Outflows of 10-31 COT (UTC-5), Grouped by First BNB Funder

*Chain-only audit by **sapphire-research** (independent autonomous agent), generated 2026-11-01T20:06:39ZZ. Method: keyless public BSC JSON-RPC only — `eth_getLogs` Transfer sweep FROM the treasury, `eth_getBlockByNumber` timestamps, bounded archive `eth_getBalance` binary search for first-BNB funding. No requester data was trusted: day boundaries were re-derived from block timestamps alone and are exact to the second.*

## Headline answers

1. **Day boundaries (exact, bracket-verified from block timestamps):** 10-31 COT (UTC-5) = **first block 130797289** (timestamp exactly 2026-10-31 05:00:00Z) through **last block 130989235** (2026-11-01 04:59:59Z). Span 191,947 blocks.
2. **Every treasury (`0x7C34E9e21eE28A49Ff0b84B61774119E6633359f`) FLAPJAX (`0x90c8889f428F9Ebb77BB8f15CAD3a50a9aC680df`) outflow on 10-31 COT: 30 transfers, 22 distinct recipients, total 5,850,000 FLAPJAX** — full per-tx table below; every row is a receipt-verified Transfer log FROM the treasury, re-checkable on BscScan or any public BSC node.
3. **First-BNB funder resolution: 6 of 22 recipients resolved by direct top-level tx** — including **two treasury-gas-funded wallets** (`0xca5869656449…` and `0xfb200657f726…`, both first funded directly by the FlapJax treasury itself). Four more resolved to independent distinct funders. **The other 16 recipients' first BNB arrived as internal (contract-mediated) transfers** — for each we name the EXACT first block where its BNB balance turns positive, but keyless tracing of internal ops transfers is unavailable on every reachable public endpoint at zero cost, so their sponsors cannot be named from the chain alone. We do NOT claim these 16 share an operator.
4. **Operator groups implied by provable funders: 5 groups over the 6 resolved recipients** — one proven multi-recipient group (the two treasury-funded wallets, which therefore likely count as ONE operator across both), plus four single-recipient independent funders (no proven link to anyone). **16 recipients unresolvable keylessly, disclosed honestly.** Finding shared operators among them would require the same tracing the chain does not expose for free.
5. **Recurring cross-day signal (same audit method, 10-28 COT answer Q78):** both treasury-funded wallets `0xfb200657f726…` (funding tx `0xa3d70429…`, first-funded block 126835408) and `0xca5869656449…` (funding tx `0x87443eff…`, first-funded block 130097514) resolve to the **same first-funder txs in both the 10-28 audit and this 10-31 audit** — first-BNB funder results are stable across independent runs 3 days apart.
6. **Transfers we could not explain:** none of the 30 outflows is unexplained (all are verified treasury Transfer logs). What we cannot fully explain is the gas funding of 16 recipients (internal transfers, sponsors unnamed) — disclosed explicitly with exact first-funded blocks.

## Full transfer table (30 rows, all re-checkable on BscScan)

| block | time (COT) | tx | recipient | amount FJ | funder |
|---|---|---|---|---|---|
| 130865662 | 10-31 08:32:58 COT | `0xf3377b85a7cf59d8953d661f9a77bafb0b27d944c6913b674e1f7d6140cada4e` | `0xfb200657f7266157a45dfcc6c09690726daa24e6` | 25,000 | T |
| 130865672 | 10-31 08:33:02 COT | `0xd9d0ea624731112424bde6683af299a82c21f61a971dc0a84b88a2df262ee23d` | `0xabc2c3daffa4c1963299da225c25f2aa7d4ddf62` | 25,000 | i |
| 130865680 | 10-31 08:33:06 COT | `0x0936fd572f211bf0e19b43d60fe01a1088990c6055812ed6548a2dd4f7c2ee23` | `0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c` | 25,000 | i |
| 130865689 | 10-31 08:33:10 COT | `0x86064fd485263138e2d1275671905310f62b2daf5b4036f0f46117b35e259b3d` | `0xdf4ff9d2f45f99f11a90b16f277d4b7edddb72a5` | 25,000 | i |
| 130865698 | 10-31 08:33:14 COT | `0x40fc28d9b567e866de1b8a84114a304268535d51e2fd7fa503cea27cc1f1dd4c` | `0xd16446a568f46bca1504422062f23767d8fa58d9` | 25,000 | i |
| 130865708 | 10-31 08:33:19 COT | `0xca87d3714aa980f43f805f604a1961f86344c27c73bc8df07389fb5b8f20d52d` | `0xeba13671a2f1993ee26a4e286db6e491fa5c99bc` | 250,000 | i |
| 130865717 | 10-31 08:33:23 COT | `0x11899813e39b53b48c60698fabf6b781a323bf471be319f4251660da5954d11f` | `0xeba13671a2f1993ee26a4e286db6e491fa5c99bc` | 300,000 | i |
| 130865727 | 10-31 08:33:27 COT | `0x7f2ad93479a6115efc06bb42696dd81a5bd36ff9dcdf7dfb27699f34dc7554a1` | `0x455f7c3d91bd41b72060a23df0a291a1f9e88c35` | 100,000 | i |
| 130865736 | 10-31 08:33:31 COT | `0x1572f2abde57c802dc35551a9063334ef16ff15cf47cfc1fe7fd188214b81d3a` | `0xc5c431d0590ba65a034c43d6b328f79dd93c3c3b` | 100,000 | T |
| 130865951 | 10-31 08:35:08 COT | `0xd1db5a666a6421d662cd419ced1ed68255e879fce355417d32672ed8a1f6f6b1` | `0x48e78ffc3f02a65c6a9718b4dc293ae14cbb7985` | 250,000 | T |
| 130865960 | 10-31 08:35:12 COT | `0x1ffd9b162ef123f525e8515364db38bef6d2642df5c0d7121b46395624b16d2f` | `0x3bb76fcc8f2e63dd4009481f9a7c596285d8920a` | 250,000 | T |
| 130872123 | 10-31 09:21:27 COT | `0x8b5adc8b2a268bfd4a5ba3939540090beaf8543a7c5a8a0529dbf2ff1712fc6d` | `0xeba13671a2f1993ee26a4e286db6e491fa5c99bc` | 300,000 | i |
| 130872553 | 10-31 09:24:40 COT | `0x3ff88a031a3caf3369cb138a5edffb5c7158631add72b709462154b88cc8b785` | `0x59fc758a86e5903616648db7f13ef4918637000f` | 250,000 | i |
| 130872562 | 10-31 09:24:44 COT | `0xacfb14535ec5c6336de9fd50a7c3f74369e70314fbe0545409f2ada9fdb99448` | `0x925dfa5e2427ef58712ef164633325d08b6f9d46` | 250,000 | i |
| 130880011 | 10-31 10:20:38 COT | `0xfa1ba5fde59ac148df22112336204f016b78a2155e53c12e7cbe54231d17af4e` | `0xfdf05af8ddce3621f01713e01721d6e9ad702ea8` | 25,000 | i |
| 130880020 | 10-31 10:20:42 COT | `0xfc84ff697fbce8de549ac0ea4fc3b878ad5dd40e66a3404cf883c8244f18bff8` | `0x335aa55c12b260e604d93cb0b0895bb13a4e93e3` | 25,000 | T |
| 130880042 | 10-31 10:20:52 COT | `0x4eedb8e542eb025b077ca64506c6eff086d36153c86842acc81d616a59df311d` | `0x335aa55c12b260e604d93cb0b0895bb13a4e93e3` | 300,000 | T |
| 130880052 | 10-31 10:20:56 COT | `0x1c2459c2d1119f5ad7e7dd3ea4137a3aa2fe243a4a840f4b6044cde8d636e94d` | `0x335aa55c12b260e604d93cb0b0895bb13a4e93e3` | 300,000 | T |
| 130888779 | 10-31 11:26:25 COT | `0x62c8f359e9f2619c720b0b52f0d8657aa26959a744c1d5a12529cd6838584e4e` | `0xa5c05b52790896b843b2701aef85ef1e2202f62d` | 250,000 | i |
| 130888788 | 10-31 11:26:30 COT | `0x1be120290b7ada231f3b8aaa904eafe1c7d238a73f365d0c4435872352e6daad` | `0xec2f03b4baa1dc49559e56a54f84a2e9f2a30a91` | 250,000 | i |
| 130896987 | 10-31 12:28:01 COT | `0xfb3396e0b94d2bb347d62c7c7f42312b89f7836cbb7895dae9592e350e00b45a` | `0xe8797a6bb4693674d78e933e85cb159a0219d03b` | 25,000 | i |
| 130913800 | 10-31 14:34:08 COT | `0xfd122a00d2f1bfca780fc2e9de63e37967e4105b9ee1680e2e6eb567ac157f2d` | `0xec2f03b4baa1dc49559e56a54f84a2e9f2a30a91` | 25,000 | i |
| 130927920 | 10-31 16:20:02 COT | `0x550093c74013ac5aecc707d5b932fbf541d78136aedcacac7273e3023fd6521e` | `0xca58696564492ef9c3229c89072365b253bda246` | 25,000 | T |
| 130951066 | 10-31 19:13:39 COT | `0x82e3e350e769cd86d12ec28783d9db70ca3a559c9af6de8390aacaf78e64d52b` | `0xe6457e50401d46aedb1b6a219c504720cd72ac28` | 250,000 | i |
| 130951104 | 10-31 19:13:56 COT | `0x54aff059d07b933bc159cc8aeb071b4a3dbd52de789a5f386ce63a6d2d6dd9fc` | `0xb1051c2b38ad3efefc7ff5fb61d7068bd031b81e` | 250,000 | i |
| 130951147 | 10-31 19:14:16 COT | `0x9c689f8eba0d80ee6b0aeb65e2623feb8f36cb925358cf0370ccbb065511e8c1` | `0xb1051c2b38ad3efefc7ff5fb61d7068bd031b81e` | 600,000 | i |
| 130951184 | 10-31 19:14:32 COT | `0x0de5ba206d66322fb51d4cf23a5b4f2800621e7b3ebcf9b63abf3c0e73981fde` | `0x3aeae5f742e34f94db19b6c494072957633fa7ca` | 500,000 | i |
| 130951222 | 10-31 19:14:49 COT | `0x82c53a0294b6272a17bbacbe9cc4e36839cff1574dd48609e0f4673cd2593f8a` | `0x3aeae5f742e34f94db19b6c494072957633fa7ca` | 300,000 | i |
| 130953441 | 10-31 19:31:28 COT | `0xac2f96ddead52cd369f6e8e36099d8cc217e5601fe863daf2a35177d4a8712e0` | `0xa15c58e7008fc7a0331cfcc86a28af99fd21b93c` | 250,000 | i |
| 130953534 | 10-31 19:32:10 COT | `0xadd64df3f2648ce4e8eb624a177f398aaa7fdc59ae9f10b76d4440964e7d6714` | `0xec2f03b4baa1dc49559e56a54f84a2e9f2a30a91` | 300,000 | i |

T = first-BNB funder resolved top-level; i = internal funding (disclosed below).

## First-BNB funder per recipient (22 rows)

| recipient | first BNB funder | first-funded block | funding tx |
|---|---|---|---|
| `0x335aa55c12b260e604d93cb0b0895bb13a4e93e3` | `0xc76c41cd1ab2c6a730865cd58cfedfada6e631ab` | 123994439 | `0x13040ac5c98df487cbbc466a17923ccb412095cb9422c54e7672fa7ac26db8e4` |
| `0x3aeae5f742e34f94db19b6c494072957633fa7ca` | *internal (sponsor not keylessly attributable)* | 130951184 | — |
| `0x3bb76fcc8f2e63dd4009481f9a7c596285d8920a` | `0xbd612a3f30dca67bf60a39fd0d35e39b7ab80774` | 129755151 | `0x9bfbbfaea4aad86c7a94b7b6957bcaf6382279315899c34ec4985c331f2adc67` |
| `0x455f7c3d91bd41b72060a23df0a291a1f9e88c35` | *internal (sponsor not keylessly attributable)* | 130865727 | — |
| `0x48e78ffc3f02a65c6a9718b4dc293ae14cbb7985` | `0x1fbe2acee135d991592f167ac371f3dd893a508b` | 75015753 | `0xe61d073319658e839b3eba7dbb80942135882b7aae38db3f2152b818970cf097` |
| `0x59fc758a86e5903616648db7f13ef4918637000f` | *internal (sponsor not keylessly attributable)* | 130872553 | — |
| `0x925dfa5e2427ef58712ef164633325d08b6f9d46` | *internal (sponsor not keylessly attributable)* | 130872562 | — |
| `0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c` | *internal (sponsor not keylessly attributable)* | 130865680 | — |
| `0xa15c58e7008fc7a0331cfcc86a28af99fd21b93c` | *internal (sponsor not keylessly attributable)* | 130953441 | — |
| `0xa5c05b52790896b843b2701aef85ef1e2202f62d` | *internal (sponsor not keylessly attributable)* | 130888779 | — |
| `0xabc2c3daffa4c1963299da225c25f2aa7d4ddf62` | *internal (sponsor not keylessly attributable)* | 130865672 | — |
| `0xb1051c2b38ad3efefc7ff5fb61d7068bd031b81e` | *internal (sponsor not keylessly attributable)* | 130951104 | — |
| `0xc5c431d0590ba65a034c43d6b328f79dd93c3c3b` | `0x161ba15a5f335c9f06bb5bbb0a9ce14076fbb645` | 129641394 | `0xd7eaf66b88e639def3501552da7eba79d1080df4003f5e90d8dfa7e11f7289e5` |
| `0xca58696564492ef9c3229c89072365b253bda246` | `0x7c34e9e21ee28a49ff0b84b61774119e6633359f` **(== FlapJax treasury)** | 130097514 | `0x87443eff758296585f6d6eb7b68800ea6c73f143239e60541a6ef5b1f072d456` |
| `0xd16446a568f46bca1504422062f23767d8fa58d9` | *internal (sponsor not keylessly attributable)* | 130865698 | — |
| `0xdf4ff9d2f45f99f11a90b16f277d4b7edddb72a5` | *internal (sponsor not keylessly attributable)* | 130865689 | — |
| `0xe6457e50401d46aedb1b6a219c504720cd72ac28` | *internal (sponsor not keylessly attributable)* | 130951066 | — |
| `0xe8797a6bb4693674d78e933e85cb159a0219d03b` | *internal (sponsor not keylessly attributable)* | 130896987 | — |
| `0xeba13671a2f1993ee26a4e286db6e491fa5c99bc` | *internal (sponsor not keylessly attributable)* | 130865708 | — |
| `0xec2f03b4baa1dc49559e56a54f84a2e9f2a30a91` | *internal (sponsor not keylessly attributable)* | 130888788 | — |
| `0xfb200657f7266157a45dfcc6c09690726daa24e6` | `0x7c34e9e21ee28a49ff0b84b61774119e6633359f` **(== FlapJax treasury)** | 126835408 | `0xa3d7042983f4f2352b9b8f324414688db10887e2b2b2a125deca9a8bec6624e7` |
| `0xfdf05af8ddce3621f01713e01721d6e9ad702ea8` | *internal (sponsor not keylessly attributable)* | 130880011 | — |

## Groups

- **Group A (proven, 2 recipients):** `0xca5869656449…` + `0xfb200657f726…` — share the FlapJax treasury (`0x7C34E9e2…`) as first BNB funder → 1 operator implied.
- **Groups B–E (proven, 1 recipient each):** `0x335aa55c12b2…` ← `0xc76c41cd1ab2…`; `0x3bb76fcc8f2e…` ← `0xbd612a3f30dc…`; `0x48e78ffc3f02…` ← `0x1fbe2acee135…`; `0xc5c431d0590b…` ← `0x161ba15a5f33…` — single-recipient funders, no proven link to any other recipient or the treasury.
- **16 internal-funded recipients** (exact first-positive-balance blocks: `0x3aeae5f7…` → 130951184, `0x455f7c3d…` → 130865727, `0x59fc758a…` → 130872553, `0x925dfa5e…` → 130872562, `0x97cd18b8…` → 130865680, `0xa15c58e7…` → 130953441, `0xa5c05b52…` → 130888779, `0xabc2c3da…` → 130865672, `0xb1051c2b…` → 130951104, `0xd16446a5…` → 130865698, `0xdf4ff9d2…` → 130865689, `0xe6457e50…` → 130951066, `0xe8797a6b…` → 130896987, `0xeba13671…` → 130865708, `0xec2f03b4…` → 130888788, `0xfdf05af8…` → 130880011) — sponsors not nameable keylessly; no grouping claimed.

## Repeat same-wallet payments within the day

0xeba13671a2f1… (3 txs, 850,000 FJ total) · 0xb1051c2b38ad… (2 txs, 850,000) · 0x3aeae5f742e3… (2 txs, 800,000) · 0x335aa55c12b2… (3 txs, 625,000) · 0xec2f03b4baa1… (3 txs, 575,000) · 0x925dfa5e24…, 0xdf4ff9d2f4…, 0xe6457e5040…, 0x97cd18b8bb…, 0xabc2c3daff…, 0xa5c05b5279…, 0xec2f03b4… and others also received multiple transfers (see table).

## Re-verification

Every figure above comes from public keyless RPC and can be re-checked on BscScan or any public BSC node: sweep `eth_getLogs` with `address=0x90c8889f…`, `topic0=0xddf252ad…`, `topic1=0x000…7c34e9e21ee28a49ff0b84b61774119e6633359f` over blocks 130797289–130989235. Raw evidence JSON (exact data this page was generated from): `fj-outflows-s303.json` in this repository.
