# Deploy
## Mobile deploying cheat sheet for ionic 3
### Build
#### Android
```rm -rf platforms; ionic cordova build android --prod --release```

#### iOS
```rm -rf platforms; ionic cordova build ios --prod```

### Deploy
#### Android
1. ```./zipalign -v 4 [appname-unsigned].apk [appname-signed].apk ```
2. ```java -jar apk-signer-1.8.5.jar verify [appname-signed].apk ```
3. ```./zipalign -v 4 [appname-signed-UNALIGNED].apk [appname-signed-ALIGNED].apk ```

#### iOS
1. ```open ./platforms/ios/[appname].xcodeproj```
2. (Xcode) In the project navigator > [appname].
3. In the Project editor
4. Select a signing team in "signing"
5. In the project navigator > [appname] > resources > [appname]-info.plist
6. Add the key references about your app [Full List](https://github.com/yusufgkl/Apple-list-key-references).
7. Example ```<key>NSPhotoLibraryUsageDescription</key>
<string>This app needs to access the Photo Library to update the user profile picture</string>```
8. Build the app and verify if no errors displaying.
8. Product > Archive > [wait...] > publish to app store
