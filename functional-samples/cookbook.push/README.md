# Service worker with push notification

This sample demonstrates using the [Push API](https://developer.mozilla.org/en-US/docs/Web/API/Push_API) with `self.registration.pushManager.subscribe()` and specifically how to use `userVisibleOnly` to silence required notifications when receiving a push message in a service worker based extension.

## Overview

By calling a method in the sample and using an external push server website we can simulate an extension receiving a push message where it is not required to emit a notification by setting (`userVisibleOnly = false`) on registration.

## Running this extension

Note: This sample requires Chrome 132+. Before Chrome 132, the same code works with the additional requirement of the `notification` extension permission.

1. Clone this repository.
1. Go to the [web push test server](https://web-push-codelab.glitch.me/) and copy the “Public Key” to the `APPLICATION_SERVER_PUBLIC_KEY` variable in background.js.
1. Load this directory in Chrome as an [unpacked extension](https://developer.chrome.com/docs/extensions/mv3/getstarted/development-basics/#load-unpacked).
1. Click “service worker (Inactive)” on the extension to load DevTools for background.js
1. In DevTools call: `await subscribeUserVisibleOnlyFalse();`
1. Copy the output after “Subscription data to be sent to the push notification server:” and paste it into the [web push test server](https://web-push-codelab.glitch.me/) inside “Subscription to Send To” text box
1. Enter some text into “Text to Send”
1. Click “SEND PUSH MESSAGE”
1. Observe that there is no notification with the text you sent in the browser and no generic notification notification being shown by the browser (that is usually enforced). You’ll see the text you sent in the DevTools log proving the extension service worker received the push data.
