---
sidebar_position: 1
---
***
## getSignContentByAddressAndPlatform()
```javascript
getSignContentByAddressAndPlatform(address: string, platform: string): Promise<string>;
```
## params for getSignContentByAddressAndPlatform method 
Properties|Type|Value|Default|Description|Required
---|:----:|:----:|:-----:|:-----:|:---------:|
|platform|string|twitter,<br />discord,<br />opensea,<br />swapchat|no|The platform <br /> that will use<br />the sdk, <br /> currently supports <br /> twitter, <br />discord, <br />opensea, <br />swapchat|yes
|address |string|MataMask address|no|MataMask address|yes
## getTokenAfterSign()
```javascript
getTokenAfterSign(signResult: string, address: string, signContent: string, userAvatar?: string): Promise<string | undefined>;
```
## params for the getTokenAfterSign method
Properties|Type|Value|Default|Description|Required
---|:----:|:----:|:-----:|:-----:|:---------:|
|signResult|string||no|the return value of MetaMask personal_sign Method request |yes
|address |string|MataMask address|no|MataMask address|yes
|signContent |string| the return value from getSignContentByAddressAndPlatform method |no|the return value from getSignContentByAddressAndPlatform method|yes
## Usage
```javascript
import SwapChatSdk from 'swap-chat-js';

const onClickHandle = async () => {
    let accountResult = await SwapChatSdk.getEthAccount();
    if (!accountResult.address) {
      return;
    }
    console.log('accountResult', accountResult);
    let signContent = await SwapChatSdk.getSignContentByAddressAndPlatform(
      accountResult.address,
      'swapChat',
    );
    console.log('signContent', signContent);
    const signature = await window.ethereum.request({
      method: 'personal_sign',
      params: [signContent, accountResult.address, 'swapchat'],
    });
    let token = await SwapChatSdk.getTokenAfterSign(
      signature,
      accountResult.address,
      signContent,
    );
    console.log('token', token);
  };
```

## Using  in react

```javascript
import SwapChatSdk from 'swap-chat-js';
import react from "react";
function App() {
  const const onClickHandle = async () => {
    let accountResult = await SwapChatSdk.getEthAccount();
    if (!accountResult.address) {
      return;
    }
    console.log('accountResult', accountResult);
    let signContent = await SwapChatSdk.getSignContentByAddressAndPlatform(
      accountResult.address,
      'swapChat',
    );
    console.log('signContent', signContent);
    const signature = await window.ethereum.request({
      method: 'personal_sign',
      params: [signContent, accountResult.address, 'swapchat'],
    });
    let token = await SwapChatSdk.getTokenAfterSign(
      signature,
      accountResult.address,
      signContent,
    );
    console.log('token', token);
  };
  return (
    <div className="App">
     <button onClick={onClickHandle}>get token</button>
    </div>
  );
}

export default App;
```
## Using  in vue
```html
<template>
  <div class="hello">
    <button @click="onClickHandle">get token</button>
  </div>
</template>
<script>
import { getCurrentInstance} from 'vue';
import SwapChatSdk from 'swap-chat-js'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  methods: {
   async onClickHandle(event) {
    let accountResult = await SwapChatSdk.getEthAccount();
    if (!accountResult.address) {
      return;
    }
    console.log('accountResult', accountResult);
    let signContent = await SwapChatSdk.getSignContentByAddressAndPlatform(
      accountResult.address,
      'swapChat',
    );
    console.log('signContent', signContent);
    const signature = await window.ethereum.request({
      method: 'personal_sign',
      params: [signContent, accountResult.address, 'swapchat'],
    });
    let token = await SwapChatSdk.getTokenAfterSign(
      signature,
      accountResult.address,
      signContent,
    );
    console.log('token', token);
    
  }
}
}
</script>
```