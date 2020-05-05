# BlockChain Demo

This is blockchain project using Node.js to demonstrate basic idea behind blockchain technology.

In order to run the project, first open one terminal execute: 
```
npm run dev
```

The **Genesis block** has been provided like below:
```
{
    "timestamp": "Genesis time",
    "lastHash": "-----",
    "hash": "f1r57-h45h",
    "data": []
}
```

Open another terminal and run: 
```
HTTP_PORT=3002 P2P_PORT=5002 PEERS=ws://localhost:5001 npm run dev
```

Use __Curl__ or __Postman__ to post test data:

```
curl --location --request POST 'localhost:3001/mine' \
--header 'Content-Type: application/json' \
--data '{
	"data": "asdf"
}'
```

The two peer servers will sync their chains automatically by socket.

## Dynamic difficulty of mining

To see the dynamic difficulty of mining, run: `npm run dev-test`

You will notice the rate of adding block can determine the difficulty of the mining.

__Example__: 
* initial difficulty: 4
* mine rate: 3000 miliseconds.
```
Block -
            Timestamp : 1588193028112
            Last Hash : 0004876759
            Hash      : 0000baa671
            Nonce     : 179976
            Difficulty: 4
            Data      : guan 3
        
Block -
            Timestamp : 1588193028133
            Last Hash : 0000baa671
            Hash      : 00000fcdb3
            Nonce     : 2440
            Difficulty: 5
            Data      : guan 4
        
Block -
            Timestamp : 1588193032098
            Last Hash : 00000fcdb3
            Hash      : 0000068093
            Nonce     : 459547
            Difficulty: 4
            Data      : guan 5
```

## With Wallet and Transaction Pool function added

Each user has a wallet contain their own public/private key and balance.
Also with transaction pool added, transactions can be added into the pool without added into the blockchain.

**To create a new transaction:**
```
curl --location --request POST 'localhost:3001/transactions'
--header 'Content-Type: application/json'
-d '{
	"data": "asdf"
}'
```

**Get transactions**
```
curl --location --request GET 'localhost:3002/transactions'
```
