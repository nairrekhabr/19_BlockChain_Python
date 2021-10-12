# 19_BlockChain_Python
The project involves transacting over blockchain Ethereum &amp; Test BitCoins using python coding.

### Create the project folder Wallet.
### Complete the pre-installments required for the project(Refer Installation Instruction in requirement.txt)
    a. HD Wallet Derive Installation
    b. Blockchain TX Installation
    c. PHP Installation
    d. Python Bitcoin Library
    e. Python Ethereum Library
    
###  Setup constants

- In a separate file, `constants.py`, set the following constants:
  - `BTC = 'btc'`
  - `ETH = 'eth'`
  - `BTCTEST = 'btc-test'`

- In `wallet.py`, import all constants: `from constants import BTC, BTCTEST, ETH`

- Use these anytime you reference these strings, both in function calls, and in setting object keys.

###  Generate a Mnemonic

- Generate a **new** 12 word mnemonic using `hd-wallet-derive` or by using [this tool](https://iancoleman.io/bip39/).

- Set this mnemonic as an environment variable by storing it a an `.env` file and importing it into your `wallet.py`.

### Derive the wallet keys

Wallet.py files runs all the functions which interact with hd-wallet-derive using the command line. The function below calls out the dictionary of coins with addresses and privkeys.

def derive_wallets(coin=BTC, mnemonic=mnemonic, depth=3):
    p = subprocess.Popen(
        f"./derive -g --mnemonic='{mnemonic}' --coin={coin} --numderive={depth} --format=json",
        stdout=subprocess.PIPE,
        shell=True)
    (output, err) = p.communicate()
    p_status = p.wait()
    return json.loads(output)
    
 coins = {
    ETH: derive_wallets(coin=ETH),
    BTCTEST: derive_wallets(coin=BTCTEST),
}

pprint(coins)

- When done properly, running the wallet.py  the final object should look something like this

{'btc-test': [{'address': 'n45VqiDaT4R9WCe5fGMoW74ZsSaWWCgWyA',
               'index': 0,
               'path': "m/44'/1'/0'/0/0",
               'privkey': 'cRTceGbr1yp3XAPCUhmo1UsNByZ2rL5YPQrFgvEpWsPoyyo19qHD',
               'pubkey': '0220a6428ab158f2cd454c02057266d09222f891e6e9c3004965f5a6f90a882767',
               'pubkeyhash': 'f77a6940a979411119cccced6b681362c3db6a04',
               'xprv': 'tprv8jDpzBJzB7fMEXavmLRURKFjyPUFjUSoJTdcQMuVLP1zYZdjrAY5Bi4wgPz8RwZYz9PWFVXSHbioHPqNun7Dt5WK7MMoRqafR38aHwrYWeE',
               'xpub': 'tpubDFus8bMEKVM27zciez64piurYQzBtodhsmEPgswnkepPP3tWUZMfNCgorWJSsYHp7VuNpYfAiCA2dd1WvX6Pj5ZzAx1Gxt4TiU4J8XG8936'},
              {'address': 'n25obABzVfPwnxNEB24JFFq1waNZnPQwA9',
               'index': 1,
               'path': "m/44'/1'/0'/0/1",
               'privkey': 'cV5gDqwA4oY8oHPWwHkmvhzp41ABegnaGYQDhrsz3w3hijBDke7Q',
               'pubkey': '03ff6fdba3d1cb4c0bdc1b89a1acd0096488ec5dea5307182eb993562ee663aa51',
               'pubkeyhash': 'e198f9cc95b2d4ea3c49c9a69b71f47cbe609de0',
               'xprv': 'tprv8jDpzBJzB7fMGooj7iusbG6HKSCN8i4HJwJwCV2XhC33WhoKGDaRHVM3mLD42AhCX2ttsoct8My2CXpUdxSyYuHRRj9nsn4riBtry6hN4hM',
               'xpub': 'tpubDFus8bMEKVM2AGqX1NaTzfkPtTiJJ3FBtEuiV14q7TqSMC45tcQ1TyxuwVLe6zSp5JE8vbSKcheHE5DTar4ke3FnDyxFzmKruftBWyjKbYX'},
              {'address': 'mnabvJwhctVcM3jnw8R8Pd5JtQsYLTGtkD',
               'index': 2,
               'path': "m/44'/1'/0'/0/2",
               'privkey': 'cVaowifWnHBduhovoE4foXVxyNdG3G1vgM1779JRxWVGsfCTGuPo',
               'pubkey': '03056c49ec5d3fb0f00de33c5c49e45d1024cb3fc2a5741c5a78e11d356a25cc50',
               'pubkeyhash': '4d7989464a08d311401f398fbb1c81311853f8bd',
               'xprv': 'tprv8jDpzBJzB7fMK9LTxyPkQTqPeFZa6aNNqfErX64iajDLQ2Y2fnk46wGNFAVTQPfXZzb3WVUydbHswZTdh1kPKs1wLVLtNwTXMeFywKNr5va',
               'xpub': 'tpubDFus8bMEKVM2CcNFrd4LosVWDH5WFuZHQxqdoc72111jEWnoJBZeHRtERHcLPWxKyyHD4PhyKuCT3khfstRTWsuubZzzWjF9fY32mQHZu1r'}],
 'eth': [{'address': '0x14B367F42c68F9503C73853E75d0338036Defd59',
          'index': 0,
          'path': "m/44'/60'/0'/0/0",
          'privkey': '0x8fb83ee71a09a7e81d9e5196cbfe7ba927303e2a849ea51eed2132b697d3965d',
          'pubkey': '03be721ee6fcba56364ce80462aac058d622be93db58f540959ca87297b18a87bb',
          'pubkeyhash': '4b8bcca00e3fc78edf72f8a8065cfbde1216cb52',
          'xprv': 'xprvA4BLDCwe4amS6iCTF9cgoh6qYNNsMfQLx2VbYJL1oUiRf5RxFGHkB7YRkuwSVhsPkPF39U42iSky4pSXikPQQdn8MKUo7npqw9vv8Ua6tLU',
          'xpub': 'xpub6HAgciUXtxKjKCGvMB9hAq3a6QDMm88CKFRCLgjdMpFQXsm6nobziurucDGXfktWHvPPvFf3RMKfxuuyVr3GFugUxe5qvGFw6xYYTR25ry3'},
         {'address': '0xEc3aFB60C77E31f7e6905A6fEB6033550EF54Ed7',
          'index': 1,
          'path': "m/44'/60'/0'/0/1",
          'privkey': '0x3c3e2a5bbacdea9967fcf2ad13cdaf753d69c942fd09e57ec33a87a9ec70a080',
          'pubkey': '02d693f2b9224ebfab310c500b6d4f266733abd3cd4063d69806d13f4b62da42ab',
          'pubkeyhash': '8b7a500d8005e1a71a65175e4876a17faf2064d3',
          'xprv': 'xprvA4BLDCwe4amS8bVSywsFzbRcCfeGeCfdAoGfVANsQ3ywba7LvQVrkTKATy7BQ1vko4hQbCdNc2gEzJZWKdRupVmmpWz2WPRdxzpShsh8NXg',
          'xpub': 'xpub6HAgciUXtxKjM5Zv5yQGMjNLkhUm3fPUY2CGHYnUxPWvUNSVTwp7JFdeKFJv83yCKVA4dbA3LKK8AZm5qqndHvtGCgubsBVug8eRz3LpeYC'},
         {'address': '0x644070416c1e7A2b44FfF53219Ec7318628F18D0',
          'index': 2,
          'path': "m/44'/60'/0'/0/2",
          'privkey': '0x26d9a668dc28d4754c8a6de98d73a7c0c282afd6192744096603e469d9d8b21c',
          'pubkey': '02029530a9f83114b7ae9aca41f29ce96276a881ec2fe09c75cbe8d02509fc343f',
          'pubkeyhash': 'c158f33e1fa253d114ba8db5cdd2c383d6fe1318',

To transfer money from one account to another you will need to run send_tx functions.
    
    def send_tx(coin, account, to, amount):
    if coin == ETH:
        raw_tx = create_tx(coin, account, to, amount)
        signed = account.signTransaction(raw_tx)
        return w3.eth.sendRawTransaction(signed.rawTransaction)
    if coin == BTCTEST:
        raw_tx = create_tx(coin, account, to, amount)
        signed = account.sign_transaction(raw_tx)
        return NetworkAPI.broadcast_tx_testnet(signed)
        <img width="707" alt="2 1_Bitcoin_Python_Send_Transaction_2021-10-12 at 1 01 49 PM" src="https://user-images.githubusercontent.com/83980061/137013038-95c9638e-db76-4fb3-8aba-2b04e86b8d92.png">

        <img width="1437" alt="2 2_Bitcoin_Send_TX2_Python_2021-10-12 at 1 02 07 PM" src="https://user-images.githubusercontent.com/83980061/137013069-631761d7-8636-48e8-a1c5-989784258677.png">


###  Send some BITCOIN transactions!

- Now, you should be able to fund these wallets using testnet faucets. 

- Refer folder: "Wallet/Project Steps Screenshot" for stepwise BITCOIN Transactions.
     1. 1_Creation of Project &  HD-Wallet_derive folder  2021-10-06 at 10.33.42 AM
     2. 2_Run Wallet.py Python Code 2021-10-08 at 3.11.06 PM
     3. 3_BTCTEST Transaction 2021-10-08 at 9.18.50 PM
     4. 4_BTCTEST Transaction_ 2021-10-08 at 9.20.53 PM
     5. 5_BTCTEST Transaction 1 Confirmed 2021-10-08 at 9.26.56 PM
     6. 6_BTCTEST SUCCESS 2021-10-08 at 9.28.45 PM

## Send some ETHEREUM Transaction

- **Local PoA Ethereum transaction**
 
 1. Start the Blockchain Nodes(Node 1 & Node 2) as per instruction in the requirement.txt
 2. During the creation of genesis configuration prefund one of the local ETH account generated by running wallet.py (Example :  0x644070416c1e7A2b44FfF53219Ec7318628F18D0)
 3. Refer the folder-"Wallet/Project Steps Screenshot" for stepwise Ethereum Transactions in MyCrypto.
     1. 7_Ethereum_Transaction Setup Custom Network  2021-10-10 at 4.53.03 PM
     2. 8_Ethereum_Prefunded  to Generated Wallet Account 2021-10-10 at 4.57.51 PM
     3. 9_Ethereum_Send Transaction_1 To Generated Wallet Account 2021-10-10 at 4.59.28 PM
     4. 10_Ethereum_Confirm Send Transaction 1 2021-10-10 at 4.59.59 PM
     5. 11_Ethereum_Check Send Transaction_1 Status2021-10-10 at 5.18.37 PM
     6. 12_Ethereum_successfull_Transaction 1 2021-10-11 at 12.31.17 AM
     7. 13_Ethereum_Successfull send Transaction 1 2021-10-10 at 5.05.18 PM
     8. 14_Ethereum_Send Transaction 2 to  generated Wallet account 2021-10-10 at 5.17.45 PM
     9. 15_Ethereum _Confirm Send Transaction 2 2021-10-10 at 5.18.19 PM
     10. 16_Ethereum_Check Send Transaction 2 Status 2021-10-10 at 5.00.33 PM
     11. 17_Ethereum_Successfull Transaction_2 2021-10-11 at 12.30.42 AM
     12. 18_Ethereum_Successful Send To Account Transaction 2  2021-10-10 at 5.20.45 PM
 
 






    
