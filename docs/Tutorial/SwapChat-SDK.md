# SwapChat-SDK

# Intro

This article will show you how to use swapchat-sdk to successfully create various types of chat rooms, such as 1v1 private chats, group chats, twitter spaces based group chats, opensea collection based group chats, and single NFT based threads.

> You can install and experience swapchat in chrome first
>
> Downloads: https://chrome.google.com/webstore/detail/swapchat/cljogniamdljbpeapjdbdigbjmipfpgh

#### Install swapchat-sdk

```shell
npm install swap-chat-js
or
yarn add swap-chat-js
```

## Official start

> You need to create an instance of SwapChatSdk Pass in two dom elements as parameters.

> The first element is the trigger that brings up the element and the second element is the slot container for the chat tool

```javascript
import SwapChatSdk from 'swap-chat-js';
const options = {}
const params = {}
const SwapChatSdkStance = new SwapChatSdk({
    dom1,
    dom2,
    options,
    params
  }
    );
//  Methods requiring calls to instances instance.exect()
SwapChatSdkStance.exect()
```

### React Demo

#### Twitter 1v1 chat
```javascript
const params = {
  platform: "twitter",
  type: "single",
  room_payload: {
    user_name: "SwapChatNFT",
    user_avatar:
      "https://pbs.twimg.com/profile_images/1506560330876731393/tLk4jXKq_400x400.jpg",
  },
};
```

#### Group chat with Twitter space
```javascript
const params = {
      platform: 'twitter',
      type: 'group',
      room_payload: {
        space_id: '1BdxYwElXVoGX',
        space_title: '测试3',
      },
    };
```
#### Opensea 1v1 chat 
```javascript
const params = {
      platform: 'opensea',
      type: 'single',
      room_payload: {
        user_name: 'king250',
      },
    };
```
#### Group chat with opensea collection
```javascript
const params = {
      platform: 'opensea',
      type: 'group',
      room_payload: {
        collection_name: 'founders-coins',
      },
    };
```
####  Opensea nft item create thread chat  
```javascript
const params = {
      platform: 'opensea',
      type: 'thread',
      room_payload: {
        opensea_coll_slug: 'yoloholiday',
        opensea_item_token_id: '4096',
        opensea_item_contract_address:
          '0xb5643598496b159263c67bd0d25728713f5aad04',
        chain_name: 'ethereum',
      },
    };
```
####  Discord 1v1 chat  
```javascript
const params = {
      platform: 'discord',
      type: 'single',
      room_payload: {
        user_name: '方庭',
        user_id: '3162',
      },
    };
```

```tsx
import SwapChatSdk from "swap-chat-js";
import react, { useEffect, useRef } from "react";
function App() {
  const buttonRef = useRef();
  const containRef = useRef();
  useEffect(() => {
    const styleOptions = {
        width: 400,
        height: 600,
    }
    const SwapChatSdkStance = new SwapChatSdk(
      buttonRef.current,
      containRef.current,
      styleOptions,
      params
    );
    SwapChatSdkStance.exect();
  }, []);
  return (
    <div className="App">
      <button ref={buttonRef}>swapChat</button>
      <div ref={containRef}></div>
    </div>
  );
}

export default App;
```

## Using swapchat-js in vue

```html
<template>
  <div class="hello">
    <button ref="button"></button>
    <div ref="container"></div>
  </div>
</template>
<script>
import { getCurrentInstance } from "vue";
import SwapChatSdk from "swap-chat-js";
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  mounted() {
    const instance = getCurrentInstance();
    const SwapChatSdkStance = new SwapChatSdk(
      instance.refs.button,
      instance.refs.container,
      {
        width: 400,
        height: 600,
      },
      {
        platform: "discord",
        type: "single",
        room_payload: {
          user_name: "方庭#3162",
          //  space_id: '1MYxNnoyanwxw',
        },
      }
    );
    SwapChatSdkStance.exect();
  },
};
</script>
```
