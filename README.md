# google_auth

1. Install `https://pub.dev/packages/google_sign_in`
2. Set Up Google login in console. (Already set up for this test app.)
3. Paste 
    ``` xml
    <?xml version="1.0" encoding="utf-8"?> <resources> <string name="default_web_client_id">141814326588-2tpqj39b32vh1gqfkmn89knu4shpcoit.apps.googleusercontent.com</string> </resources>
    ```
    inside android/app/src/main/res/values/strings.xml
4. Add implementation 'com.google.android.gms:play-services-auth:20.4.1' in in android/app/build.gradle, under the dependencies.
5. Call this method to get id token.
```dart
const List<String> scopes = <String>[
'email',
];

GoogleSignIn googleSignIn = GoogleSignIn(
    scopes: ['email', "https://www.googleapis.com/auth/userinfo.profile"],
    clientId: "141814326588-lq0ptgh82957kpp42832ojue309imhfc.apps.googleusercontent.com");

GoogleSignInAccount? account = await googleSignIn.signIn();
GoogleSignInAuthentication? authentication = await account?.authentication;
String? idToken = authentication?.idToken;
```
