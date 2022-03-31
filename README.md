# How to add WEB3 Connection to Tribe react sdk
### example version

document for tribe starter app -> [read here](https://github.com/mosi-sol/tribe-starter-app/blob/master/README.md)

tribe 2 documents for react & starter + demo -> [watch here](https://relay.tribeplatform.com/)

**step by step doing the following code** 

1- add ethersjs package [requirment for connecting to the blockchain by using wallet in this example]
```
yarn add ethers
```

2- add web3.tsx file in -> src/component
```
import './Web3.css';
import { useState } from 'react';
import { ethers } from 'ethers';

// function Web3() {
  export const Web3 = () => {

  const [walletAddress, setWalletAddress] = useState("");

  // https://metamask.io Requests access to the user's META MASK WALLET
  async function requestAccount() {
    console.log('Requesting account...');

    if(window.ethereum) {
      console.log('detected');

      try {
        const accounts = await window.ethereum.request({
          method: "eth_requestAccounts",
        });
        setWalletAddress(accounts[0]);
      } catch (error) {
        console.log('Error connecting...');
      }

    } else {
      alert('Meta Mask not detected');
    }
  }

  async function connectWallet() {
    if(typeof window.ethereum !== 'undefined') {
      await requestAccount();

      const provider = new ethers.providers.Web3Provider(window.ethereum);
    }
  }

  return (
    <div className="Web3">
        <span><button
        
        onClick={requestAccount}
        
        >Request Account</button></span>
        <span> &nbsp; <b>Wallet Address: {walletAddress}</b></span>
    </div>
  );
}

export default Web3;
```

3- add Web3.css file in -> src/component
```
.Web3 button{
    background: #3af;
    padding: 5px;
    border-radius: 5px;
    color: azure;
    text-shadow: 1px 2px 0 #345;
}

.Web3 b{
    text-shadow: 1px 2px 0 #f1f1f1;
    color: #345;
    background: #e1e1e1;
    box-shadow: 1px 2px 3px #345;
    padding: 5px;
    border-radius: 5px;
}
```

4- add next code parameters at line 68 into App.tsx
```
<nav className="flex justify-center lg:mt-2">
  <div><Web3 /></div>
</nav>
```

5- run command to compile & test
```
yarn install
yarn start
```

6- i am not react developer, you watch an error, close that. then click on **Request Account** button for connect to the blockchain by using metamask wallet

7- after fixing the error, run build command:
```
yarn build
```

## disclaimer
i am not tribe developer yet, this repository just for test.


#
---
# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `yarn start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.\
You will also see any lint errors in the console.

### `yarn test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `yarn build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `yarn eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).
