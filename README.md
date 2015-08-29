# Javeo Polymer Chat

#### 1. Pobranie zależności
```
 $ npm install
 $ bower install
```

#### 2. Uruchomienie aplikacji
```
 $ gulp serve
```

#### 3. Przełączenie się na czystą aplikację
```
 $ git checkout beginning
 $ git checkout -b chat
```

#### 4. Utworzenie nowego komponentu
##### app/elements/my-chat/my-chat.html
```html
<dom-module id="my-chat">
    <script>
        Polymer({
            is: 'my-chat'
        });
    </script>
</dom-module>
```

#### 5. Zaimportowanie własnego komponentu
##### app/elements/elements.html
```html
<link rel="import" href="my-chat/my-chat.html">
```

#### 6. Użycie własnego komponentu
##### app/index.html
```html
<section data-route="home">
    <paper-material elevation="1">
        <my-chat></my-chat>
    </paper-material>
</section>
```

#### 7. Podłączanie się do Firebase
##### app/elements/my-chat/my-chat.html
```html
<template is="paper-material" elevation="1">
    <firebase-collection id="chat" data="{{messages}}" location="https://glaring-inferno-8663.firebaseio.com/chat">
    </firebase-collection>
</template>
```

#### 8. Wyświetlanie wiadomości
##### app/elements/my-chat/my-chat.html
```html
<template is="dom-repeat" items="{{messages}}">
    <div>
        <strong>{{item.user}}</strong>:
        <span>{{item.message}}</span>
    </div>
</template>
```

#### 9. Wpisywanie wiadomości
##### app/elements/my-chat/my-chat.html
```html
<div class="layout horizontal">
    <paper-input id="message" label="Say something..." class="flex"></paper-input>
    <paper-button raised on-tap="send">Send</paper-button>
</div>
```

#### 10. Okno logowania do czatu
##### app/elements/my-chat/my-chat.html
```html
<paper-dialog id="login" modal>
   <paper-input id="nick" label="Input your nick..." class="flex"></paper-input>
   <paper-button raised on-tap="login">Login</paper-button>
</paper-dialog>
```

#### 11. Wysyłanie wiadomości
##### app/elements/my-chat/my-chat.html
```js
send: function (e) {
   this.$.chat.add({
       user: this.$.nick.value,
       message: this.$.message.value
   });
   this.$.message.value = "";
}
```

#### 12. Logowanie do czatu
##### app/elements/my-chat/my-chat.html
```js
ready: function() {
   this.$.login.toggle();
},

login: function() {
   this.$.login.toggle();
}
```
