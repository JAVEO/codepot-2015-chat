# Javeo Polymer Chat

#### Pobranie zależności
```
 $ npm install
 $ bower install
```

#### Uruchomienie aplikacji
```
 $ gulp serve
```

#### Przełączenie się na czystą aplikację
```
 $ git checkout beginning
 $ git checkout -b chat
```

#### Utworzenie nowego komponentu
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

#### Zaimportowanie własnego komponentu
##### app/elements/elements.html
```html
<link rel="import" href="my-chat/my-chat.html">
```

#### Użycie własnego komponentu
##### app/index.html
```html
<section data-route="home">
    <paper-material elevation="1">
        <my-chat></my-chat>
    </paper-material>
</section>
```

#### Podłączanie się do Firebase
##### app/elements/my-chat/my-chat.html
```html
<template is="paper-material" elevation="1">
    <firebase-collection id="chat" data="{{messages}}" location="https://glaring-inferno-8663.firebaseio.com/chat">
    </firebase-collection>
</template>
```

#### Wyświetlanie wiadomości
##### app/elements/my-chat/my-chat.html
```html
<template is="dom-repeat" items="{{messages}}">
    <div>
        <strong>{{item.user}}</strong>:
        <span>{{item.message}}</span>
    </div>
</template>
```

#### Wpisywanie wiadomości
##### app/elements/my-chat/my-chat.html
```html
<div class="layout horizontal">
    <paper-input id="message" label="Say something..." class="flex"></paper-input>
    <paper-button raised on-tap="send">Send</paper-button>
</div>
```

#### Okno logowania do czatu
##### app/elements/my-chat/my-chat.html
```html
<paper-dialog id="login" modal>
   <paper-input id="nick" label="Input your nick..." class="flex"></paper-input>
   <paper-button raised on-tap="login">Login</paper-button>
</paper-dialog>
```

#### Wysyłanie wiadomości
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

#### Logowanie do czatu
##### app/elements/my-chat/my-chat.html
```js
ready: function() {
   this.$.login.toggle();
},

login: function() {
   this.$.login.toggle();
}
```
