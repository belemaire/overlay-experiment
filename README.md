### Setup

1. `git clone`
2. `yarn install`
3. `ern run-android`

### Trying App / Explanations

- Build / Launch app
- Accept overlay permission if first time install
- Click on `CREATE CHAT HEAD` button
- Open the 'chat' Activity (a MiniApp) by clicking on the chat overlay button
- You can see **Initial text** text on the MiniApp main screen
- Click `UPDATE TEXT` button
- Kill MiniApp Activity (remove it from the task list)
- Click the chat overlay button
- You can notice that the text now reads **Updated text**

The text is set as a [global variable](https://github.com/belemaire/overlay-experiment/blob/master/App.js#L19). This demonstrates that even if MiniApp Activity is destroyed (unmounted), the JS VM is not terminated, so the global state is retained. This works also if the state is kept in a redux store. This example is not using redux , not even React state, for the sake of simplicity, but as long as the state is not explicity cleared applicatively or recreated from an initial state in the constructor of the component, it will still be there, and next time the MiniApp is recreated, it will render using the retained state.

Most of the Android code has been copied from this article :
https://medium.com/@kevalpatel2106/create-chat-heads-like-facebook-messenger-32f7f1a62064
