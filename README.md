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