---
sidebar_position: 1
---
***

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