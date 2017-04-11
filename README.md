[![Published on webcomponents.org](https://img.shields.io/badge/webcomponents.org-published-blue.svg)](https://beta.webcomponents.org/element/PolymerElements/paper-button)

##&lt;emojione-selector&gt;

A polymer element that works best as a emoji picker and is powered by the emojione library

Example:

<!---
```
<custom-element-demo>
  <template>
    <script src="bower_components/webcomponentsjs/webcomponents-lite.js"></script>
    <link rel="import" href="bower_components/polymer/polymer.html">
    <link rel="import" href="bower_components/iron-flex-layout/iron-flex-layout.html">
    <link rel="import" href="bower_components/iron-ajax/iron-ajax.html">
    <link rel="import" href="bower_components/iron-icon/iron-icon.html">
    <link rel="import" href="bower_components/iron-icons/iron-icons.html">
    <link rel="import" href="bower_components/iron-icons/social-icons.html">
    <link rel="import" href="bower_components/iron-list/iron-list.html">
    <link rel="import" href="bower_components/iron-collapse/iron-collapse.html">
    <link rel="import" href="bower_components/bower_components/paper-styles/color.html">
    <link rel="import" href="bower_components/paper-icon-button/paper-icon-button.html">
    <link rel="import" href="bower_components/paper-button/paper-button.html">
    <link rel="import" href="bower_components/paper-input/paper-input.html">
    <link rel="import" href="bower_components/paper-item/paper-icon-item.html">

    <link rel="import" href="emojione-selector.html">
    <template>
      <style is="custom-style">
        :host {
          @apply(--layout-vertical);
          @apply(--layout-fullbleed);
        }

        iron-list {
          @apply(--layout-flex);
          padding: 0 8px;
          background-color: var(--paper-grey-100);
        }

        iron-list .message {
          display: inline-block;
          padding: 8px;
          border-radius: 3px;
          background-color: var(--paper-grey-300);
          margin-top: 8px;
        }

        iron-list .message.right {
          float: right;
        }

        iron-list .message img {
          vertical-align: middle;
          height: 24px;
          width: 24px;
        }

        .demo-bottom {
          @apply(--layout-horizontal);
          @apply(--layout-end);
          padding: 8px;
        }

        paper-input {
          @apply(--layout-flex);
          --paper-input-container-focus-color: var(--paper-blue-500);
          margin: 0 8px;
        }

        paper-button {
          background-color: var(--paper-blue-500);
          color: #fff;
          margin-bottom: 8px;
        }

        emojione-selector {
          --emojione-selector-iron-list: {
            background-color: var(--paper-grey-50);
          }
          --paper-input-container-focus-color: var(--paper-blue-500);
          --paper-tabs-selection-bar-color: var(--paper-blue-500);
        }

      </style>
      <iron-ajax url="messages.json" last-response="{{messages}}" auto></iron-ajax>

      <iron-list id="messages" items="[[messages]]" as="item">
        <template>
          <div>
            <div class$="message [[item.side]]">
              <span inner-h-t-m-l="{{getMessage(item.message)}}"></span>
            </div>
          </div>
        </template>
      </iron-list>
      <iron-collapse opened="{{opened}}">
        <emojione-selector opened="{{opened}}" emoji="{{emoji}}"></emojione-selector>
      </iron-collapse>
      <div class="demo-bottom">
        <paper-icon-button id="emojiButton" icon="{{computeIfChatIcon(opened)}}" src="{{computeIfChatImg(opened)}}" title="emoji"></paper-icon-button>
        <paper-input label="Type something" value="{{message}}" no-label-float></paper-input>
        <paper-button id="send" raised>Send</paper-button>
      </div>
    </template>
    <script>
      Polymer({
        is: 'x-demo',

        properties: {
          opened: {
            type: Object
          },
          message: {
            type: String
          },
          emoji: {
            type: String,
            observer: 'onEmojiChange'
          }
        },

        listeners: {
          'emojiButton.tap': 'onEmojiButtonTap',
          'send.tap': 'onSendButtonTap'
        },

        ready: function () {
          // HACK force re-render of iron list
          this.async(function () {
            this.$.messages.notifyResize();
          }, 600);
        },

        computeIfChatIcon: function (opened) {
          if (opened) {
            return '';
          } else {
            return 'social:mood';
          }
        },

        computeIfChatImg: function (opened) {
          if (opened) {
            return 'https://cdn.jsdelivr.net/emojione/assets/png/263a.png?v=2.2.7';
          } else {
            return '';
          }
        },

        getMessage: function (message) {
          return emojione.toImage(message);
        },

        onEmojiChange: function () {
          if (this.emoji) {
            this.message = this.message + this.emoji;
          }
        },

        onEmojiButtonTap: function () {
          this.opened = !this.opened;
        },

        onSendButtonTap: function () {
          if (this.message) {
            this.push('messages', {
              'side': 'right',
              'message': this.message
            });
            this.message = '';
          }
        }
      });
    </script>
</custom-element-demo>
```
-->
```html
<iron-ajax url="messages.json" last-response="{{messages}}" auto></iron-ajax>

<iron-list id="messages" items="[[messages]]" as="item">
  <template>
    <div>
      <div class$="message [[item.side]]">
        <span inner-h-t-m-l="{{getMessage(item.message)}}"></span>
      </div>
    </div>
  </template>
</iron-list>
<iron-collapse opened="{{opened}}">
  <emojione-selector opened="{{opened}}" emoji="{{emoji}}"></emojione-selector>
</iron-collapse>
<div class="demo-bottom">
  <paper-icon-button id="emojiButton" icon="{{computeIfChatIcon(opened)}}" src="{{computeIfChatImg(opened)}}" title="emoji"></paper-icon-button>
  <paper-input label="Type something" value="{{message}}" no-label-float></paper-input>
  <paper-button id="send" raised>Send</paper-button>
</div>
```
