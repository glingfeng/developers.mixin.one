---
title: Websocket Messages
category: Mixin Messenger
order: 13
---

Following is message category supported by Websocket.

PLAIN_TEXT 
```json
  {
    "id": "UUID // generated by client", 
    "action":  "CREATE_MESSAGE",
    "params": {
      "conversation_id": "UUID",
      "category": "PLAIN_TEXT",
      "status": "SENT",
      "message_id": "UUID // generated by client",
      "data": "Base64 encoded data" ,
    }
  }
```

PLAIN_IMAGE
```json
  {
    "id": "UUID",
    "action": "CREATE_MESSAGE",
    "params": {
      "conversation_id": "UUID"
      "category": "PLAIN_IMAGE"
      "status": "SENT",
      "message_id": "UUID",
      "data": "Base64 encoded data"
    }
  }
 ```

Date Format
```js
  // width: int, height: int, size: int64
  {"attachment_id": "Read From POST /attachments", "mime_type": "", "width": 1024, "height": 1024, "size": 1024, "thumbnail": "base64 encoded"}
```

PLAIN_DATA
```json
  {
    "id":  "UUID",
    "action":  "CREATE_MESSAGE",
    "params": {
      "conversation_id": "UUID",
      "category": "PLAIN_DATA",
      "status": "SENT",
      "message_id": "UUID",
      "data": "Base64 encoded data",
    }
  }
```
Data Format
```js
  // size int64
  {"attachment_id": "Read From POST /attachments", "mime_type": "", "size": 1024, "name": "Share"}
```

PLAIN_STICKER
```json
  {
    "id":  "UUID",
    "action":  "CREATE_MESSAGE",
    "params": {
      "conversation_id": "UUID",
      "category": "PLAIN_STICKER",
      "status": "SENT",
      "message_id":  "UUID",
      "data": "Base64 encoded data"
    }
  }
```
Data Format
```json
  {"name": "hello", "album_id": "UUID"}
```

PLAIN_CONTACT
```json
  {
    "id": "UUID",
    "action": "CREATE_MESSAGE",
    "params": {
      "conversation_id": "UUID",
      "category": "PLAIN_CONTACT"
      "status": "SENT",
      "message_id": "UUID",
      "data":  "Base64 encoded data"
    }
  }
```
Data Format
```json
 { "user_id": "UUID"}
```

APP_BUTTON_GROUP
```json
  {
    "id": "UUID",
    "action": "CREATE_MESSAGE",
    "params": {
      "conversation_id": "UUID",
      "category": "APP_BUTTON_GROUP",
      "status": "SENT",
      "message_id": "UUID",
      "data": "Base64 encoded data"
    }
  }
```
Data Format
```js
  [{"label": "Mixin Website", "color": "#ABABAB", "action": "https://mixin.one"}, ...]
```

APP_CARD
```json
  {
    "id": "UUID",
    "action": "CREATE_MESSAGE",
    "params": {
      "conversation_id": "UUID",
      "category": "APP_CARD",
      "status": "SENT",
      "message_id": "UUID",
      "data": "Base64 encoded data"
    }
  }
```
Data Format
```json
  {"icon_url": "https://mixin.one/assets/98b586edb270556d1972112bd7985e9e.png", "title": "Mixin", "description": "A free and lightning fast peer-to-peer transactional network for digital assets.", "action": "https://mixin.one"}
```
PLAIN_VIDEO
```json
  {
    "id": "UUID",
    "action": "CREATE_MESSAGE",
    "params": {
      "conversation_id": "UUID",
      "category": "PLAIN_VIDEO",
      "status": "SENT",
      "message_id": "UUID",
      "data": "Base64 encoded data"
    }
  }
```
Data Format
```js
 // width: int, height: int, size: int64, duration: int64 milliseconds
 {"attachment_id": "Read From POST /attachments", "mime_type": "", "width": 1024, "height": 1024, "size": 1024, "duration": 1024, "thumbnail": "base64 encoded"}
```

`ACKNOWLEDGE_MESSAGE_RECEIPT` ack server received message
```json
  {
    "id": "UUID",
    "action": "ACKNOWLEDGE_MESSAGE_RECEIPT",
    "params": {
      "message_id": "UUID // message_id is you received message's message_id",
      "status": "READ"
    }
  }
```

`CREATE_PLAIN_MESSAGES` send a batch of messages, max size 100.
```js
  {
    "id": "UUID",
    "action": "CREATE_PLAIN_MESSAGES",
    "params": {
      "messages": [
        {
          "conversation_id": "UUID",
          "recipient_id": "UUID",
          "message_id": "UUID",
          "representative_id": "UUID (optional, only supported in peer to peer conversation)",
          "quote_message_id": "UUID (optional, only supported text, e.g. PLAIN_TEXT)",
          "category": "Only support plain category e.g.: PLAIN_TEXT, PLAIN_STICKER etc",
          "data": "Correspond to category."
        },
        ...
      ]
    }
  }
```

```
// Sample Response
{
  "id": "89e0bdee-c355-47f2-945a-be48be875606",
    "action": "CREATE_PLAIN_MESSAGES",
    "params": "mRm5rm9bkQztvpsaTyz1Rib0BEM0S1FKl",
}
```
