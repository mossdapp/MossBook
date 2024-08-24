# Modular wallets

Moss defines modular smart contract wallets as follows:

The main features are divided into four layers:

*   **Abstract Account Layer**

    This layer forms the foundation of the smart contract wallet, responsible for executing transactions, verifying signatures, enabling social recovery, and handling gas paymaster.
*   **State Storage Layer**

    As a smart contract wallet, it is essential to maintain necessary states such as public keys, user personalization settings, and extended application features. These states are stored within the smart contract address of the user’s account.
*   **Own Dapp Management Layer**

    Users manage their applications independently and can freely choose the Own Dapps they need.
*   **Own Dapp Logic Layer**

    The specific application logic is an independent contract address, which only allows the implementation of code logic and prohibits any state storage.

Existing contract wallets have only implemented the first two functionalities and cannot extend any application.

As a modular wallet, Moss can provide the expansion scheme. Any contract wallet project that integrates the Own Dapp management mechanism can expand its users' limitless possibilities.

Moss, as a solution, decouples these functionalities in modular wallets. Moss can serve as part of a modular stack, with multiple possibilities for the arrangement of modules.
