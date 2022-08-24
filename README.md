#  Dapp on ICP

## Available Scripts

In the project directory, you can run:

### `yarn start`



#### Connecting Address

```js

const injectEarth = () => {
  return new Promise((resolve, reject) => {
    window.addEventListener('load', () => {
      if (window.earth) {
        resolve(window.earth);
      } else {
        reject(new Error('ICP dAPP not installed.'));
      }
    });
  });
};
const handleEarthEnable = () => {
  await injectEarth();
    window?.earth
    .enable().then((account) => {
        console.log("Successfully connected to ICP Dapp", account);
      })
      .catch((err) => {
        console.error(err);
      });
  };
```

#### Triggering Canister Sign Messages

```js

 const callSignMessage = async () => {
    try {
      let response = await window.earth.signMessage({
        canisterId: 'ury7f-eqaaa-aaaab-qadlq-cai',
        method: 'say',
        args: 'hello'
      });
      console.log(response)
    } catch (error) {

    }
  }
  const callSignMessageBatch = async () => {
    try {
      let response = await window.earth.signMessage([
      {
        canisterId: 'ury7f-eqaaa-aaaab-qadlq-cai',
        method: 'say',
        args: 'hello'
      }, 
      { canisterId: 'tde7l-3qaaa-aaaah-qansa-cai', 
        method: 'availableCycles'
       }]);
      console.log(response)
     } catch (error) {

    }
  }
```