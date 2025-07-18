# DecentralizedMint: A MEV-Resistant On-Chain NFT Marketplace

DecentralizedMint provides a fully decentralized NFT marketplace built on Ethereum. It features on-chain royalty enforcement, atomic swaps for secure trading, and a sophisticated order book designed to mitigate MEV (Miner Extractable Value) exploitation. This project aims to offer a transparent, secure, and efficient platform for NFT creators and collectors.

This repository contains the Python scripts and smart contract code that power DecentralizedMint. Unlike traditional centralized marketplaces, DecentralizedMint ensures creators retain control over their work and receive royalties directly on-chain without reliance on intermediaries. Our atomic swap functionality guarantees that assets are exchanged simultaneously, eliminating counterparty risk. The unique order book implementation is engineered to minimize opportunities for front-running and other MEV strategies, creating a fairer trading environment for all participants. We prioritize gas efficiency through meticulous contract design and optimization techniques.

DecentralizedMint leverages cutting-edge blockchain technology to address the limitations of existing NFT marketplaces. It's designed to be a permissionless and open-source alternative, promoting accessibility and community involvement. The codebase is structured for maintainability and extensibility, allowing for future enhancements and integrations with other decentralized applications. This project empowers creators to monetize their NFTs while maintaining autonomy and control.

## Key Features

*   **On-Chain Royalty Enforcement:** Royalties are enforced directly within the smart contract logic, ensuring creators automatically receive their designated percentage of each sale. The `setRoyalty()` function in the `NFTContract.sol` allows NFT creators to set their desired royalty percentage (up to a maximum limit). The `transfer()` function automatically calculates and distributes royalties during the transfer of ownership.
*   **Atomic Swaps:** The `swap()` function in `Marketplace.sol` allows for the trustless exchange of NFTs for Ether (or other ERC20 tokens). The function verifies that both parties have deposited their respective assets into the contract before executing the transfer, guaranteeing a secure and simultaneous swap.
*   **MEV-Resistant Order Book:** Implemented using a priority queue data structure within the smart contract (`OrderBook.sol`). The order book design prioritizes fair order execution by minimizing front-running opportunities through techniques like order randomization and batch execution.
*   **Gas-Optimized Smart Contracts:** The Solidity code has been carefully optimized for gas efficiency. Techniques such as minimizing state variable updates, using efficient data structures, and utilizing assembly code for computationally intensive operations have been employed to reduce transaction costs.
*   **Comprehensive Python SDK:** The `decentralizedmint.py` provides a Python interface for interacting with the smart contracts. This SDK simplifies the process of deploying contracts, minting NFTs, creating orders, and executing trades. It handles the complexities of transaction signing and blockchain communication.
*   **Decentralized Governance:** Future versions will incorporate a decentralized governance system to allow token holders to propose and vote on changes to the marketplace parameters and functionality.
*   **Support for ERC-721 and ERC-1155:** The marketplace is designed to be compatible with both ERC-721 and ERC-1155 NFT standards, providing flexibility for creators and collectors.

## Technology Stack

*   **Solidity:** The programming language used to write the smart contracts that govern the marketplace logic. Solidity is a statically-typed, contract-oriented, high-level language for implementing smart contracts on the Ethereum blockchain.
*   **Python:** Used for developing the client-side SDK, deployment scripts, and testing frameworks. Python's versatility and extensive libraries make it ideal for interacting with the blockchain.
*   **Web3.py:** A Python library for interacting with the Ethereum blockchain. It provides the necessary tools for connecting to Ethereum nodes, signing transactions, and deploying smart contracts.
*   **Hardhat:** A development environment for compiling, deploying, testing, and debugging Ethereum software. Hardhat provides a local Ethereum network for rapid development and testing.
*   **Ganache:** A personal Ethereum blockchain for local development. Ganache allows developers to simulate real-world blockchain conditions without the need for a live network.
*   **OpenZeppelin Contracts:** A library of secure and reusable smart contracts for Ethereum. OpenZeppelin Contracts provide implementations for common standards like ERC-721 and ERC-1155.

## Installation

1.  **Clone the repository:**

    git clone https://github.com/ezozu/DecentralizedMint.git
    cd DecentralizedMint

2.  **Install Python dependencies:**

    python3 -m venv venv
    source venv/bin/activate
    pip install -r requirements.txt

3.  **Install Node.js dependencies:**

    npm install -g npm@latest
    npm install --save-dev hardhat @nomicfoundation/hardhat-toolbox dotenv

4.  **Compile the smart contracts:**

    npx hardhat compile

## Configuration

1.  **Create a `.env` file:**

    Create a `.env` file in the root directory of the project and add the following environment variables:

    PRIVATE_KEY="your_ethereum_private_key"
    INFURA_API_KEY="your_infura_api_key"
    NETWORK="sepolia"  # or "mainnet", "goerli", etc.

2.  **Configure Hardhat:**

    Modify the `hardhat.config.js` file to configure the network settings, including the RPC URL and chain ID.

## Usage

1.  **Deploy the smart contracts:**

    Use the `deploy.py` script to deploy the smart contracts to the chosen network.

    python deploy.py

    The script will output the contract addresses.

2.  **Interact with the contracts using the Python SDK:**

    

Detailed API documentation for the `DecentralizedMint` class, including all available functions and their parameters, is available in the `docs/sdk_documentation.md` file.

## Contributing

We welcome contributions to DecentralizedMint! Please follow these guidelines:

*   Fork the repository.
*   Create a new branch for your feature or bug fix.
*   Write clear and concise commit messages.
*   Submit a pull request with a detailed description of your changes.
*   Ensure all tests pass before submitting your pull request.
*   Adhere to the coding style and conventions used in the project.

## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/ezozu/DecentralizedMint/blob/main/LICENSE) file for details.

## Acknowledgements

We would like to thank the following projects and individuals for their contributions to the development of DecentralizedMint:

*   The Ethereum Foundation for providing the platform and tools for building decentralized applications.
*   The OpenZeppelin team for their secure and reusable smart contracts.
*   The Hardhat team for their excellent development environment.