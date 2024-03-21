# 3040Crypto Wallet API

## API Description

The 3040Crypto Wallet API is designed to streamline and enhance the experience of using 3040Crypto's services. This API facilitates efficient interactions with users' crypto wallets, including balance inquiries, transaction histories, and initiating transfers. By offering this API, 3040Crypto aims to become the preferred crypto wallet service, ensuring speed, security, and ease of use.

## List of Endpoints with Parameters

### 1. Wallet Balance

- **Endpoint:** `/wallet/balance`
- **Method:** GET
- **Parameters:**
  - `wallet_id`: Unique identifier for the user's wallet.
- **Description:** Returns the current balance of the specified wallet in various cryptocurrencies.

### 2. Transaction History

- **Endpoint:** `/wallet/transactions`
- **Method:** GET
- **Parameters:**
  - `wallet_id`: Unique identifier for the user's wallet.
  - `limit`: (Optional) Number of transactions to return. Defaults to 10.
- **Description:** Retrieves a list of recent transactions for the specified wallet, including amounts, transaction types, and dates.

### 3. Initiate Transfer

- **Endpoint:** `/wallet/transfer`
- **Method:** POST
- **Parameters:**
  - `from_wallet_id`: Sender's wallet identifier.
  - `to_wallet_id`: Recipient's wallet identifier.
  - `amount`: Amount of cryptocurrency to transfer.
  - `currency`: The type of cryptocurrency to transfer.
- **Description:** Initiates a transfer of a specified amount of cryptocurrency from one wallet to another.

## Description of Resources

### Wallet Balance Resource

This resource provides information about the current balance of a user's wallet. The response includes a status message indicating the success of the request, a data object containing the wallet balance details, and a message confirming the successful fetching of the wallet balance. The `walletBalance` object within `data` includes the `wallet_id` and an array of `balances`, each with a `currency` and its corresponding `amount`.

```json
{
  "status": "success",
  "data": {
    "walletBalance": {
      "wallet_id": "abc123",
      "balances": [
        {"currency": "BTC", "amount": "0.5"},
        {"currency": "ETH", "amount": "2.0"},
        {"currency": "3040C", "amount": "1000"}
      ]
    }
  },
  "message": "Wallet balance fetched successfully."
}
```
### Transaction History Resource

This resource returns a user's recent transaction history. The response structure is similar to the wallet balance, including a status, a data object containing the `transactionHistory`, and a success message. The `transactionHistory` object lists transactions, each with a `transaction_id`, the `amount` transferred (noting currency), the `type` of transaction (send or receive), and the transaction date.

```json
{
  "status": "success",
  "data": {
    "transactionHistory": {
      "wallet_id": "abc123",
      "transactions": [
        {
          "transaction_id": "tx10001",
          "amount": "-0.1 BTC",
          "type": "send",
          "date": "2024-03-18T10:00:00Z"
        },
        {
          "transaction_id": "tx10002",
          "amount": "0.2 ETH",
          "type": "receive",
          "date": "2024-03-17T14:30:00Z"
        }
      ]
    }
  },
  "message": "Transaction history fetched successfully."
}
```

### Transfer Confirmation Resource
This resource confirms the initiation of a transfer between wallets. It informs the user of the success status, provides data including the `transferConfirmation` object, and a message confirming the initiation. The `transferConfirmation` details the `from_wallet_id`, `to_wallet_id`, `amount` (with currency), `currency` explicitly stated, `transaction_id`, and the current status of the transfer (e.g., pending).

```json
{
  "status": "success",
  "data": {
    "transferConfirmation": {
      "from_wallet_id": "abc123",
      "to_wallet_id": "def456",
      "amount": "0.1 BTC",
      "currency": "BTC",
      "transaction_id": "tx10003",
      "status": "pending"
    }
  },
  "message": "Transfer initiated successfully."
}
```

### Sample Request and Response

#### Request: Retrieve Wallet Balance
To retrieve the balance of a specific wallet, send a GET request to the `/wallet/balance` endpoint with the wallet's unique identifier.

```http
GET /wallet/balance?wallet_id=abc123
```

#### Response:
The response will include the status of the request, the wallet ID, and an array listing the balances in various cryptocurrencies.

```json
{
  "status": "success",
  "data": {
    "walletBalance": {
      "wallet_id": "abc123",
      "balances": [
        {"currency": "BTC", "amount": "0.5"},
        {"currency": "ETH", "amount": "2.0"},
        {"currency": "3040C", "amount": "1000"}
      ]
    }
  },
  "message": "Wallet balance fetched successfully."
}
```



