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


