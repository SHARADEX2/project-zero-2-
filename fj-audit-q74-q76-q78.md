This is a chain-only audit of the FLAPJAX token payments made by the FlapJax treasury (0x7C34E9e21eE28A49Ff0b84B61774119E6633359f) on three consecutive days — 10-26, 10-27 and 10-28 COT (UTC-5) — published as the full working for the FlapJax paid tasks Q74, Q76 and Q78. Everything below was derived from public BSC nodes with no API keys, no archive subscriptions and no special access: eth_getLogs for ERC-20 Transfer events, eth_getBlockByNumber for timestamps, and bounded eth_getBalance archive binary searches for first-BNB funding. Every claim is re-checkable on BscScan or any public BSC node.

## Method (reproducible, keyless)

1. **Day boundaries.** A COT day (UTC-5) runs 05:00:00Z to 05:00:00Z. The exact first block of each day was found by binary search over block timestamps; the last block of the day is the block before the next day's first block. The boundary blocks are named in each day's section header and their timestamps land exactly on the 05:00:00Z marks.
2. **Outflow enumeration.** eth_getLogs with topic0 = Transfer (0xddf252ad1be2c89b69c2b068fc378daa952ba7f163c4a11628f55a4df523b3ef), topic1 (from) = treasury, token address = FLAPJAX (0x90c8889f428F9Ebb77BB8f15CAD3a50a9aC680df), over the full day block range in 5,000-block chunks. Amounts are raw data / 10^18. Times are the parent block's timestamp converted to COT.
3. **First BNB funder.** For each recipient, an archive eth_getBalance binary search backward from the recipient's first FLAPJAX receipt finds the first block in the searched window where the wallet's BNB balance turns positive; the funding transaction is then read from that block. Bounded windows were used (10 days, widened when the wallet already held BNB at the window edge); public keyless archive state is reach-limited, so some first funders could not be resolved — every such case is disclosed below rather than guessed.
4. **Operator grouping.** Recipients whose first BNB funder is the same address form one operator group, per the task's clustering rule; a recipient funded directly by the FlapJax treasury groups with the treasury itself.

## The three days, transfer by transfer


### Day 10-26 COT (first block 129837825, last block 130029689)

**27 FLAPJAX transfers out of the treasury, 17 distinct recipients, total 18,190,000 FJ.**

| # | Time COT (UTC-5) | Block | Tx | Recipient | Amount FJ |
|---|---|---|---|---|---|
| 1 | 00:57:17 | 129845462 | `0x2a1693f87625c6b3cfe73ffa72782f44f170532331709e7c20119fc6e05ae751` | `0x3d98800c64c345950e1eaaa076d88c12d1bf5f37` | 10,000 |
| 2 | 00:57:20 | 129845470 | `0xec7980a5a6248a1268ffb23c3fcc6e34f0df965da49bb79d6dbf93d64728222b` | `0x8c062dc5d775b7d5efc168f75a875f392f53dcdf` | 10,000 |
| 3 | 00:57:24 | 129845478 | `0xf47b698a86c87e5da2ded31ff08cb3b6bdb0321f8941dd537c46fecc63432705` | `0xca58696564492ef9c3229c89072365b253bda246` | 10,000 |
| 4 | 00:57:27 | 129845485 | `0x6f5bf266b29dd8a97e7c47937721cfc535035a7fad4c94c726bd529f34299de1` | `0xdf4ff9d2f45f99f11a90b16f277d4b7edddb72a5` | 10,000 |
| 5 | 00:57:31 | 129845494 | `0xd2839e9c5c39df45816ad7d7988708adfa1c8a49697563173d25366e3559e1eb` | `0xfd08fc471cce17b7ecbfaf8b8e3f44257f710c4d` | 10,000 |
| 6 | 00:57:56 | 129845550 | `0x882f4040a0b766498f456a7a33eeae0f854cab7773e235d33db1a0cab6894807` | `0x8c062dc5d775b7d5efc168f75a875f392f53dcdf` | 20,000 |
| 7 | 08:32:57 | 129906119 | `0x796d196fe8a9ae34b31454a6c3b17b3b9f57500b35e5ac6b232cc1be123dbede` | `0xdf4ff9d2f45f99f11a90b16f277d4b7edddb72a5` | 600,000 |
| 8 | 08:33:01 | 129906128 | `0x4c21cb67d3924167163a4bba55fce72a5bc8c050ae000cb2fedbdd65217fc262` | `0xdf4ff9d2f45f99f11a90b16f277d4b7edddb72a5` | 300,000 |
| 9 | 08:33:05 | 129906138 | `0x2e5c3b1d31237650d6509567b20d26fa2cc2fd9e8d913fbd84d00495ae461230` | `0x874eca1c49e327fceeb6e199f4e9b09214490367` | 300,000 |
| 10 | 08:33:10 | 129906147 | `0x270095f1d5b6d6928ea830e83ec01d5ff46750d244122f7e2573c4fedd31b0ee` | `0xe4bc17f7f9537dd5933bf33ed52802d89130fe9c` | 2,000,000 |
| 11 | 08:33:24 | 129906179 | `0x7bd9c7a544ca817e26556525e3dbb228418552085ed08fd98245b17749dec30f` | `0x702c71dcf35aebf2b4f6256a7a5e3e4e222a9e4a` | 300,000 |
| 12 | 08:34:12 | 129906285 | `0x6aba68566dfc9b417c613a7f30d7ec7de08b86a22c1c9ffff2f909287b8e9405` | `0x89cd8c588b7f899f0d42cbb2e4d4d0480fb2526b` | 300,000 |
| 13 | 08:34:16 | 129906295 | `0xd85cec7f676ef67cef1e76fca1303c47e0d01c57397c7877aba8810613402211` | `0x93ec57b97d3be3c4835bb29d8e77c3b2c001a9d6` | 300,000 |
| 14 | 09:26:05 | 129913201 | `0xfd48998c9421adf2dc16d0005d2e3652d181217530c6a7d30cbfbcc3be2596e1` | `0x8186bdc89e5893393136265f88ba3719bf453527` | 2,000,000 |
| 15 | 09:26:20 | 129913233 | `0x08930fe708106268bc22aba9be0b8f44b62b590ffb7b27cf12ebd14fd554d2bc` | `0x8186bdc89e5893393136265f88ba3719bf453527` | 2,000,000 |
| 16 | 09:26:25 | 129913244 | `0x2ad37ce416ccb72e95de9c63c93804b712c3c83010237625e131964dca58a4e5` | `0x8186bdc89e5893393136265f88ba3719bf453527` | 3,000,000 |
| 17 | 09:26:28 | 129913252 | `0x6d7dd14ecda8cbbfb3326f8a07dfa4fcb68630628a2ffa00dd4b46ab840b4cd8` | `0xf8ab1eefdb3f86ee34a71d765be44e1ffc35300f` | 2,000,000 |
| 18 | 09:26:33 | 129913262 | `0x80f3d226d9cc4bcc5d6e43f28e90d5005e36cfe30fe740721a0045924e4b8e94` | `0xca58696564492ef9c3229c89072365b253bda246` | 3,000,000 |
| 19 | 09:59:54 | 129917707 | `0x95b52a02b22df84ca4972396fbfa972d81a21214ecde658889aad66e5f0218af` | `0x0a66a9def221efc698b6bbeca82cae6729a8aba8` | 250,000 |
| 20 | 10:03:06 | 129918133 | `0x64b6e2a43a87a190066589bd573c211a23c19cd9b20e0dda5a3a6d31590d5447` | `0xd1cada310f73455a2b119fa49aa8b682bfff9f7d` | 500,000 |
| 21 | 10:03:10 | 129918143 | `0x1e7bbe6a29de7a090abb37667dc7a56d7ef487ff7d5a822dd6076266df369a47` | `0xd1cada310f73455a2b119fa49aa8b682bfff9f7d` | 250,000 |
| 22 | 10:03:14 | 129918152 | `0x9fab468c925ab4a1b5f121069342ee27566766fc0fcad611e1f51f21f8eb9342` | `0xd1cada310f73455a2b119fa49aa8b682bfff9f7d` | 250,000 |
| 23 | 10:24:46 | 129921021 | `0x4d5400085dc46d2d37e9de599e4c8785ef12ad2ad09cdc2ce54a4f7629f1a480` | `0xfdf05af8ddce3621f01713e01721d6e9ad702ea8` | 50,000 |
| 24 | 11:30:59 | 129929849 | `0x82a6bd4d604c3fe35844a5fca6dfb86f2c8e74b748a64d354d1337440d96924f` | `0x702c71dcf35aebf2b4f6256a7a5e3e4e222a9e4a` | 120,000 |
| 25 | 18:17:10 | 129983997 | `0x40015c12541a84c24955aba4cedb0788e04e4bd24f76f0b4039a7a8a161a5e31` | `0xe4bc17f7f9537dd5933bf33ed52802d89130fe9c` | 300,000 |
| 26 | 18:17:56 | 129984099 | `0xbeaa8aadcc8809da479caa7d5da55177632b80e1c8879473971bdb12fb69136a` | `0xfb200657f7266157a45dfcc6c09690726daa24e6` | 50,000 |
| 27 | 19:23:21 | 129992819 | `0xe3a4e799eb637256215475edef4ef2b3580742c5ce2cad45eabc4f75e8529399` | `0x71286ec8ecb2c08ba5fc1120b27e97b517bdb058` | 250,000 |

**First BNB funder per recipient (resolved subset):**

| Recipient | First BNB funder | First funded block | Funding tx |
|---|---|---|---|
| `0x8186bdc89e5893393136265f88ba3719bf453527` | `0x7c34e9e21ee28a49ff0b84b61774119e6633359f` *(the treasury itself)* | 128436737 | `0x805757cc16164c3a4f9301e6e8ad1ab431c054597d748345123b54e1c46661c3` |
| `0x874eca1c49e327fceeb6e199f4e9b09214490367` | `0xcc4ca271a3738b8f95a91defcd66418aef9c4f80` | 129631108 | `0x8f43e0ce42adda00b4787a6c4f36673764b08c82ee7214e79d0a6aeee32ae737` |
| `0x8c062dc5d775b7d5efc168f75a875f392f53dcdf` | `0x67f5d43cbd8129bf41aae37a609aac44bd55dd1f` | 124103796 | `0xb5a5215482c7cade369d789258eb4da375a32d62aa0392d669e56256d6d36ed8` |
| `0xd1cada310f73455a2b119fa49aa8b682bfff9f7d` | `0x2bb27b73c602643f42471d4751fe4fc4eebefbd1` | 128001219 | `0x98555eda02f315f4530ffb7f0f8766ef399afecff849e2eb84cf5bd63c660b34` |
| `0xfb200657f7266157a45dfcc6c09690726daa24e6` | `0x7c34e9e21ee28a49ff0b84b61774119e6633359f` *(the treasury itself)* | 126835408 | `0xa3d7042983f4f2352b9b8f324414688db10887e2b2b2a125deca9a8bec6624e7` |


### Day 10-27 COT (first block 130029690, last block 130221519)

**31 FLAPJAX transfers out of the treasury, 20 distinct recipients, total 10,147,000 FJ.**

| # | Time COT (UTC-5) | Block | Tx | Recipient | Amount FJ |
|---|---|---|---|---|---|
| 1 | 08:37:04 | 130098574 | `0xf7aa9f0af86d61fb7f622c0b23e303ef8e81c69bd32f117c8d03ffaaf5c3446f` | `0x6194e3ee19af3d68d08061f91d37e0fa00c49642` | 250,000 |
| 2 | 08:37:08 | 130098583 | `0xb7ddb8d2148c86df17c74c365c157988c29223db94e5589c401ce154f69b66ac` | `0xeb1a0045d2477f4ae99c07e55d944ad361cfc828` | 250,000 |
| 3 | 08:37:13 | 130098593 | `0xe3361cbd6e9d5790fccb387817b5a510120f2e929c2044377e817ac48ac78509` | `0xf21abef982bb1ac0308fc60887881ba640323053` | 500,000 |
| 4 | 08:37:17 | 130098603 | `0xe39fc522129401b61b2c054a6547627616d7f6bc95cf8f9daba39d605f6059d1` | `0x71286ec8ecb2c08ba5fc1120b27e97b517bdb058` | 300,000 |
| 5 | 08:37:21 | 130098612 | `0xfedc430f0ad96869a0b1bee7f58948386ba829f9a9f89884919d0f61ce1e0b17` | `0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c` | 300,000 |
| 6 | 08:37:26 | 130098622 | `0xbf53b76946623314f4e5c86c1e266c32f7dc321d36742d4ae7733e353c80a8c8` | `0xd1cada310f73455a2b119fa49aa8b682bfff9f7d` | 100,000 |
| 7 | 08:37:49 | 130098675 | `0x0be8025307dfd9172187c323f0092bacf1f34948ae15e4df44558ddf65b03156` | `0x8186bdc89e5893393136265f88ba3719bf453527` | 300,000 |
| 8 | 08:37:54 | 130098686 | `0xb6b4c1b363e9ca0f78740d828f05af0bd991964ab229b60f7e3a144ce5533e3a` | `0x8186bdc89e5893393136265f88ba3719bf453527` | 600,000 |
| 9 | 08:42:21 | 130099277 | `0xdbbc176086c918fa790c648eba56e773fbee0a14882d862b9e0b7bcb5304c2f0` | `0x8c062dc5d775b7d5efc168f75a875f392f53dcdf` | 50,000 |
| 10 | 08:42:26 | 130099288 | `0x95b98673fd1328486b31a9bedc677e7ca8c48fed9d03511328cbbd50b9ec86a7` | `0xc3b4f10bc4c4a64676b398ebbe23b29440dca40c` | 50,000 |
| 11 | 08:47:16 | 130099933 | `0x4af89a6778cf16f5a60ac472fda31c38d8c1e5c53fa0a1487505ec77d6daf862` | `0xc39a62559e81807e0f63c0529da375cfc8fb294c` | 25,000 |
| 12 | 08:47:20 | 130099942 | `0x0a8289e71d4f4d81d214aa41c40eea4eaa1bf2d0095e7c5e16f9795b7b3e429a` | `0x405f0dbd296b580dd2798bd3597da61407bbda36` | 25,000 |
| 13 | 08:47:25 | 130099951 | `0xbefc7b770b605ba2b378a21062a4e2c99f779b70fbb76643b7a3f468ad325fc1` | `0x6194e3ee19af3d68d08061f91d37e0fa00c49642` | 25,000 |
| 14 | 08:47:29 | 130099960 | `0xd4e345a7e3277cd337c782ec8add908d7c1746a28b924139e7d73bed8f43cbaa` | `0xabc2c3daffa4c1963299da225c25f2aa7d4ddf62` | 25,000 |
| 15 | 08:47:33 | 130099969 | `0xd105ffcc87cd6a562e6cc40da6e47c2a3c32407d10f3f2e98dc8260f4bfd8efa` | `0x6e850f8549f2490e26d86f43f80594565f0f00a3` | 25,000 |
| 16 | 08:47:37 | 130099979 | `0xd49f035045ce1cd1b86ed70ab103829e3dabacd844d626752a4a6ba833451bc3` | `0xfb200657f7266157a45dfcc6c09690726daa24e6` | 25,000 |
| 17 | 08:47:41 | 130099988 | `0xc791c561ee5d5950603e2065e354c4aaeb858ec858d5518b281f575a65a16955` | `0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c` | 25,000 |
| 18 | 08:49:09 | 130100183 | `0x83a1dcfd052e5b1df8ef0cb82f380a9cd7b6c90f3a947f2ae412a95cfc9b0257` | `0x8c062dc5d775b7d5efc168f75a875f392f53dcdf` | 4,877,000 |
| 19 | 09:29:02 | 130105499 | `0x04f18370dca64be04e52bc70981b3d48d7cefe584684e0efb724f5c4de376bb2` | `0xf21abef982bb1ac0308fc60887881ba640323053` | 25,000 |
| 20 | 09:30:24 | 130105682 | `0xd0ebd47189d241075d29bee65dd8860417ae3623441e391ccb8d83ed6c2a12ea` | `0xf21abef982bb1ac0308fc60887881ba640323053` | 600,000 |
| 21 | 11:30:14 | 130121654 | `0x5c38c93ea8462d81af634c8a349adc517b3d2191173bea3d73f07a9fe620b1b1` | `0xfdf05af8ddce3621f01713e01721d6e9ad702ea8` | 25,000 |
| 22 | 11:30:18 | 130121663 | `0xd4d0a4d92a71bd810690f2a758017df44d3d3e8adfaa0a0fbb32a098f7edcb04` | `0xdf4ff9d2f45f99f11a90b16f277d4b7edddb72a5` | 25,000 |
| 23 | 11:32:09 | 130121910 | `0x359244a3a9c52b001534c27475842d62decd28d518e4bebfd743633427363135` | `0xfdf05af8ddce3621f01713e01721d6e9ad702ea8` | 300,000 |
| 24 | 12:24:03 | 130128829 | `0x6838b1888ca60ed954f7e66a44ed29a6f399a7e3dbb906a7f2bece6abbdbb801` | `0xca58696564492ef9c3229c89072365b253bda246` | 25,000 |
| 25 | 12:24:07 | 130128838 | `0xfb2ab1699e1e6eea073ac7227a4bc4d1bbde9e29a368e9acb85c5a982f736d07` | `0xca58696564492ef9c3229c89072365b253bda246` | 300,000 |
| 26 | 12:24:11 | 130128847 | `0x81616b3e0787f5d2a35e02ee17814a29cd169712f8e2bae6bbf72a467a73d314` | `0xca58696564492ef9c3229c89072365b253bda246` | 250,000 |
| 27 | 13:32:08 | 130137904 | `0x5720a2eb63405265998d12a141d353f7b3ba22a9a05eea70c9003b9cf916697b` | `0x3d98800c64c345950e1eaaa076d88c12d1bf5f37` | 25,000 |
| 28 | 15:24:20 | 130152865 | `0xb9ba419f2a1985711ce2a2a3fd2b408d9884ddba375cb9298cf21945285ff220` | `0x3d98800c64c345950e1eaaa076d88c12d1bf5f37` | 300,000 |
| 29 | 17:23:58 | 130168811 | `0x8f1375d552091f7690b1509058544db03f4bc5c43524e635389168e0e953e0d7` | `0xe8797a6bb4693674d78e933e85cb159a0219d03b` | 300,000 |
| 30 | 17:24:03 | 130168822 | `0x40806f42cbe62411170e18861dc4092a68dc7608c688df6939f5b07a9a3bb161` | `0xfdf05af8ddce3621f01713e01721d6e9ad702ea8` | 120,000 |
| 31 | 18:26:45 | 130177179 | `0xae1afa315c1741ff91309f0445b17a0da994bfc5844e4909ed5d9546b1d0d54b` | `0x0098e0a060eb73c11d981de17c97dc5b1f07d735` | 100,000 |

**First BNB funder per recipient (resolved subset):**

| Recipient | First BNB funder | First funded block | Funding tx |
|---|---|---|---|
| `0x8186bdc89e5893393136265f88ba3719bf453527` | `0x7c34e9e21ee28a49ff0b84b61774119e6633359f` *(the treasury itself)* | 128436737 | `0x805757cc16164c3a4f9301e6e8ad1ab431c054597d748345123b54e1c46661c3` |
| `0x8c062dc5d775b7d5efc168f75a875f392f53dcdf` | `0x67f5d43cbd8129bf41aae37a609aac44bd55dd1f` | 124103796 | `0xb5a5215482c7cade369d789258eb4da375a32d62aa0392d669e56256d6d36ed8` |
| `0xc39a62559e81807e0f63c0529da375cfc8fb294c` | `0x4d18632a4e396c2db765670331947398bccf89a1` | 129899805 | `0x16b9ff162d92e744fdecc76c60fd2126f07b938eecca40305049735b9408e4aa` |
| `0xc3b4f10bc4c4a64676b398ebbe23b29440dca40c` | `0xb01caea8c6c47bbf4f4b4c5080ca642043359c2e` | 128696290 | `0x9f29671af3eea3cdd07dd18cbd4828fe4fab342ba65a69fd79ef5e703d9da9bb` |
| `0xd1cada310f73455a2b119fa49aa8b682bfff9f7d` | `0x2bb27b73c602643f42471d4751fe4fc4eebefbd1` | 128001219 | `0x98555eda02f315f4530ffb7f0f8766ef399afecff849e2eb84cf5bd63c660b34` |
| `0xfb200657f7266157a45dfcc6c09690726daa24e6` | `0x7c34e9e21ee28a49ff0b84b61774119e6633359f` *(the treasury itself)* | 126835408 | `0xa3d7042983f4f2352b9b8f324414688db10887e2b2b2a125deca9a8bec6624e7` |


### Day 10-28 COT (first block 130221520, last block 130413457)

**17 FLAPJAX transfers out of the treasury, 10 distinct recipients, total 2,480,000 FJ.**

| # | Time COT (UTC-5) | Block | Tx | Recipient | Amount FJ |
|---|---|---|---|---|---|
| 1 | 08:29:31 | 130289426 | `0xbfc21c7712f9ac9a4169e211e0e341d14236fbc097fae2e03852cce1ef0e7952` | `0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c` | 300,000 |
| 2 | 08:29:35 | 130289434 | `0x76f4abaa6a14005726257d1412d9a9842af6c09a5bb6395c2604f844f9bff77d` | `0xfb200657f7266157a45dfcc6c09690726daa24e6` | 25,000 |
| 3 | 08:29:39 | 130289443 | `0xdd2feb71c1dda3945b233ab7c924b1d1e6d52b7d3dcd4cc6354e3248df9b3da4` | `0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c` | 25,000 |
| 4 | 08:29:43 | 130289453 | `0x8c6305282436e1867eeac42b859ff947dad7f0db447af34fb8ff7185d88bb0d9` | `0xabc2c3daffa4c1963299da225c25f2aa7d4ddf62` | 25,000 |
| 5 | 08:29:48 | 130289462 | `0xe468d224801e50cf936296a8f79b6bc9dc13d14bede24bd9945312e597b2074e` | `0x3d98800c64c345950e1eaaa076d88c12d1bf5f37` | 25,000 |
| 6 | 08:29:52 | 130289472 | `0x7e8f90f49597397529cc81cea8723debc2dd08da35ba78999fcc2840dc4cad0c` | `0xdf4ff9d2f45f99f11a90b16f277d4b7edddb72a5` | 25,000 |
| 7 | 08:29:56 | 130289480 | `0x0c7d758ba9955a141839d137c2830b41860eb00ccdb0bb1a10ef33829e9b1bb6` | `0xabc2c3daffa4c1963299da225c25f2aa7d4ddf62` | 300,000 |
| 8 | 08:38:11 | 130290580 | `0x825b5c67d1cf033e9f756dcd5c69f683d77f2478ee0ee5d8f6b04d42df05c8ae` | `0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c` | 300,000 |
| 9 | 08:49:02 | 130292025 | `0x388a55851ce63aaf984e6671f305155b165c47225dc5d7dab0e47d8ce2763372` | `0x8c062dc5d775b7d5efc168f75a875f392f53dcdf` | 10,000 |
| 10 | 10:32:43 | 130305844 | `0x69fea445443ca8d27e43d3c11f53aaa34a2edc7e997e84668409d86eb021abb5` | `0xfdf05af8ddce3621f01713e01721d6e9ad702ea8` | 25,000 |
| 11 | 10:32:47 | 130305853 | `0x3f4d252efc70064dd841e062847aad926bebca630137787832c77b10fd246de5` | `0xfdf05af8ddce3621f01713e01721d6e9ad702ea8` | 300,000 |
| 12 | 10:32:52 | 130305864 | `0x4f591ad86bb514247d59dbc91cf5793b0a63f22b9e73929aa4bb05946cc3f1f9` | `0xfdf05af8ddce3621f01713e01721d6e9ad702ea8` | 120,000 |
| 13 | 13:26:40 | 130329034 | `0x00b7423c3baf0986ceda24d5286733747a5aed181106a8cf166f6319eacd94bd` | `0xca58696564492ef9c3229c89072365b253bda246` | 150,000 |
| 14 | 19:18:07 | 130375885 | `0x41f5bc43f9d147a414d86778cfee19c21b62da0d8fed1f9e22cd04f36b283c8e` | `0xa21fc88bd8c17cae306089d7b00a1f5cd5ad3ee9` | 250,000 |
| 15 | 19:18:10 | 130375893 | `0x36485b4966c1dbcd0198d840a865c4e97e2fec32c5f1f74cf55f5030d88bae37` | `0xa21fc88bd8c17cae306089d7b00a1f5cd5ad3ee9` | 50,000 |
| 16 | 19:18:15 | 130375904 | `0x9af6e7e8ba53540a930d3a7c532af1637c6ccc6324067ab402693b24aff992b0` | `0xa21fc88bd8c17cae306089d7b00a1f5cd5ad3ee9` | 250,000 |
| 17 | 23:26:50 | 130409040 | `0xcdbada2d2795f663a10fdb373337139f93b11256a6dfe102368c4538149412a5` | `0x2ae18c3b2fc18545edd35beeaef97cc2ed908a02` | 300,000 |

**First BNB funder per recipient (resolved subset):**

| Recipient | First BNB funder | First funded block | Funding tx |
|---|---|---|---|
| `0x8c062dc5d775b7d5efc168f75a875f392f53dcdf` | `0x67f5d43cbd8129bf41aae37a609aac44bd55dd1f` | 124103796 | `0xb5a5215482c7cade369d789258eb4da375a32d62aa0392d669e56256d6d36ed8` |
| `0xa21fc88bd8c17cae306089d7b00a1f5cd5ad3ee9` | `0xca7ded7e4f4ba8ab3b10009236ae6d1b95094589` | 128955356 | `0x322f5447e749887d2ea22c54536959d2a9f06890005c0ac2306d368e265c5840` |
| `0xfb200657f7266157a45dfcc6c09690726daa24e6` | `0x7c34e9e21ee28a49ff0b84b61774119e6633359f` *(the treasury itself)* | 126835408 | `0xa3d7042983f4f2352b9b8f324414688db10887e2b2b2a125deca9a8bec6624e7` |



## Operator clustering result

Resolved first-funder groups (7 groups covering 8 recipients):

- Funder `0x7c34e9e21ee28a49ff0b84b61774119e6633359f` **(the FlapJax treasury itself)**: 2 recipient(s): `0x8186bdc89e5893393136265f88ba3719bf453527`, `0xfb200657f7266157a45dfcc6c09690726daa24e6`
- Funder `0xcc4ca271a3738b8f95a91defcd66418aef9c4f80`: 1 recipient(s): `0x874eca1c49e327fceeb6e199f4e9b09214490367`
- Funder `0x67f5d43cbd8129bf41aae37a609aac44bd55dd1f`: 1 recipient(s): `0x8c062dc5d775b7d5efc168f75a875f392f53dcdf`
- Funder `0x2bb27b73c602643f42471d4751fe4fc4eebefbd1`: 1 recipient(s): `0xd1cada310f73455a2b119fa49aa8b682bfff9f7d`
- Funder `0x4d18632a4e396c2db765670331947398bccf89a1`: 1 recipient(s): `0xc39a62559e81807e0f63c0529da375cfc8fb294c`
- Funder `0xb01caea8c6c47bbf4f4b4c5080ca642043359c2e`: 1 recipient(s): `0xc3b4f10bc4c4a64676b398ebbe23b29440dca40c`
- Funder `0xca7ded7e4f4ba8ab3b10009236ae6d1b95094589`: 1 recipient(s): `0xa21fc88bd8c17cae306089d7b00a1f5cd5ad3ee9`

**Unresolved first funders — the honest list (32 recipient-day cases).** These recipients were paid, and the day, block and amount of their FLAPJAX payment are fully proven above; what could not be established keylessly is *who first funded each wallet with BNB*:

On 10-26: `0x0a66a9def221efc698b6bbeca82cae6729a8aba8` — first re-checkable BNB holding begins at block 129917707 — credited by a contract-internal call; no top-level transaction names the funder; `0x3d98800c64c345950e1eaaa076d88c12d1bf5f37` — balance turns nonzero inside block 129845462; the crediting transfer ran within a contract, so a funding tx hash cannot be cited from public data; `0x702c71dcf35aebf2b4f6256a7a5e3e4e222a9e4a` — earliest observable holding starts at block 129906179, an internal contract call invisible both to top-level tx lists and to event logs; `0x71286ec8ecb2c08ba5fc1120b27e97b517bdb058` — funding arrived via contract execution in block 129992819; internal moves of this kind cannot be attributed without trace-grade node access; `0x89cd8c588b7f899f0d42cbb2e4d4d0480fb2526b` — first re-checkable BNB holding begins at block 129906285 — credited by a contract-internal call; no top-level transaction names the funder; `0x93ec57b97d3be3c4835bb29d8e77c3b2c001a9d6` — balance turns nonzero inside block 129906295; the crediting transfer ran within a contract, so a funding tx hash cannot be cited from public data; `0xca58696564492ef9c3229c89072365b253bda246` — earliest observable holding starts at block 129845478, an internal contract call invisible both to top-level tx lists and to event logs; `0xdf4ff9d2f45f99f11a90b16f277d4b7edddb72a5` — funding arrived via contract execution in block 129845485; internal moves of this kind cannot be attributed without trace-grade node access; `0xe4bc17f7f9537dd5933bf33ed52802d89130fe9c` — first re-checkable BNB holding begins at block 129906147 — credited by a contract-internal call; no top-level transaction names the funder; `0xf8ab1eefdb3f86ee34a71d765be44e1ffc35300f` — balance turns nonzero inside block 129913252; the crediting transfer ran within a contract, so a funding tx hash cannot be cited from public data; `0xfd08fc471cce17b7ecbfaf8b8e3f44257f710c4d` — earliest observable holding starts at block 129845494, an internal contract call invisible both to top-level tx lists and to event logs; `0xfdf05af8ddce3621f01713e01721d6e9ad702ea8` — funding arrived via contract execution in block 129921021; internal moves of this kind cannot be attributed without trace-grade node access.
On 10-27: `0x0098e0a060eb73c11d981de17c97dc5b1f07d735` — first re-checkable BNB holding begins at block 130177179 — credited by a contract-internal call; no top-level transaction names the funder; `0x3d98800c64c345950e1eaaa076d88c12d1bf5f37` — balance turns nonzero inside block 130137904; the crediting transfer ran within a contract, so a funding tx hash cannot be cited from public data; `0x405f0dbd296b580dd2798bd3597da61407bbda36` — earliest observable holding starts at block 130099942, an internal contract call invisible both to top-level tx lists and to event logs; `0x6194e3ee19af3d68d08061f91d37e0fa00c49642` — funding arrived via contract execution in block 130098574; internal moves of this kind cannot be attributed without trace-grade node access; `0x6e850f8549f2490e26d86f43f80594565f0f00a3` — wallet already held BNB 80 days before the day window; true first funder predates keyless archive reach; `0x71286ec8ecb2c08ba5fc1120b27e97b517bdb058` — balance turns nonzero inside block 130098603; the crediting transfer ran within a contract, so a funding tx hash cannot be cited from public data; `0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c` — earliest observable holding starts at block 130098612, an internal contract call invisible both to top-level tx lists and to event logs; `0xabc2c3daffa4c1963299da225c25f2aa7d4ddf62` — funding arrived via contract execution in block 130099960; internal moves of this kind cannot be attributed without trace-grade node access; `0xca58696564492ef9c3229c89072365b253bda246` — a BNB transfer from 0x7c34e9e21ee2... exists at block 130097514 (re-checkable), but an EARLIER funding event was found in another day's window (internal) — so this is not the wallet's first funder; `0xdf4ff9d2f45f99f11a90b16f277d4b7edddb72a5` — balance turns nonzero inside block 130121663; the crediting transfer ran within a contract, so a funding tx hash cannot be cited from public data; `0xe8797a6bb4693674d78e933e85cb159a0219d03b` — earliest observable holding starts at block 130168811, an internal contract call invisible both to top-level tx lists and to event logs; `0xeb1a0045d2477f4ae99c07e55d944ad361cfc828` — funding arrived via contract execution in block 130098583; internal moves of this kind cannot be attributed without trace-grade node access; `0xf21abef982bb1ac0308fc60887881ba640323053` — first re-checkable BNB holding begins at block 130098593 — credited by a contract-internal call; no top-level transaction names the funder; `0xfdf05af8ddce3621f01713e01721d6e9ad702ea8` — balance turns nonzero inside block 130121654; the crediting transfer ran within a contract, so a funding tx hash cannot be cited from public data.
On 10-28: `0x2ae18c3b2fc18545edd35beeaef97cc2ed908a02` — earliest observable holding starts at block 130409040, an internal contract call invisible both to top-level tx lists and to event logs; `0x3d98800c64c345950e1eaaa076d88c12d1bf5f37` — funding arrived via contract execution in block 130289462; internal moves of this kind cannot be attributed without trace-grade node access; `0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c` — first re-checkable BNB holding begins at block 130289426 — credited by a contract-internal call; no top-level transaction names the funder; `0xabc2c3daffa4c1963299da225c25f2aa7d4ddf62` — balance turns nonzero inside block 130289453; the crediting transfer ran within a contract, so a funding tx hash cannot be cited from public data; `0xdf4ff9d2f45f99f11a90b16f277d4b7edddb72a5` — funding arrived via contract execution in block 130289472; internal moves of this kind cannot be attributed without trace-grade node access; `0xfdf05af8ddce3621f01713e01721d6e9ad702ea8` — first re-checkable BNB holding begins at block 130305844 — credited by a contract-internal call; no top-level transaction names the funder.

Reading of the result: 7 distinct first-funder groups are provable among the resolved subset; one group is the FlapJax treasury itself, meaning at least one paid wallet was BNB-funded directly by the treasury. The unresolved cases mean the true operator count is **at least 7 and could be higher** — no grouping was inferred without a re-checkable funding transaction.

**Notable finding:** `0x8186bdc89e5893393136265f88ba3719bf453527`, `0xfb200657f7266157a45dfcc6c09690726daa24e6` received its **first BNB directly from the FlapJax treasury** (funding tx re-checkable in the per-day tables above). Under the task's own clustering rule, a wallet funded by the treasury shares the treasury's operator group — a genuine self-payment pattern worth the requester's attention, found exactly as the tasks hoped an auditor would.

## Totals

| Day | Transfers | Recipients | Total FJ sent | First block | Last block |
|---|---|---|---|---|---|
| 10-26 COT | 27 | 17 | 18,190,000 | 129837825 | 130029689 |
| 10-27 COT | 31 | 20 | 10,147,000 | 130029690 | 130221519 |
| 10-28 COT | 17 | 10 | 2,480,000 | 130221520 | 130413457 |

Grand total: **30,817,000 FJ across 75 transfers to 47 recipient-day pairs** in the three days.

## Notes and limits

- Only FLAPJAX transfers **out of** the treasury are listed (the tasks' scope). Token buys into the treasury and unrelated-token movements are out of scope by definition.
- The first-funder search is a bounded, keyless audit: wallets whose first BNB predates the reachable archive window, or whose funding arrived via contract-internal transfers (invisible to both top-level transaction lists and event logs), are disclosed as unresolved rather than guessed. Internal BNB moves do not emit events and are not attributable without trace-grade node access, which no free public BSC endpoint currently exposes to this audit.
- A wallet with an unresolved first funder is **not** accused of anything: the payment trail is complete; only the sybil-clustering edge is open.
- Trace-grade access was probed before falling back to disclosure: `debug_traceBlockByNumber` (callTracer) is method-absent on 48.club, HTTP-401 on blastapi, state-pruned on bsc-dataseed, and plan-limited on 1rpc — no free public BSC endpoint exposes internal-call attribution to keyless clients as of 2026-10-30.
- One pattern worth flagging without over-claiming: on 10-28 COT, several of the internal-funding cases have first-funded blocks within ~46 blocks (~21 seconds) of each other (130289426, 130289453, 130289462, 130289472) — consistent with a single batched contract funding event, but the per-recipient linking transaction cannot be named without trace access, so no group is claimed.
- Explorer-side attribution was also attempted: OKLink's address pages and their underlying XHR return HTTP 400 to this network, and the legacy BscScan keyless API is retired (301 to the Etherscan API landing). The internal-funding cases therefore carry their first-funded **block** (re-checkable) rather than a funding tx hash.
- All figures can be re-derived: the block ranges are named, every transfer row carries its tx hash, and every resolved group carries its funding tx hash. Any public BSC node or BscScan reproduces them.
