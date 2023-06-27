# Solution

Adding this [documented manual configuration](https://github.com/expo/expo/tree/sdk-48/packages/expo-screen-orientation#configure-for-ios)
to `Info.plist` fixes the problem seen in the EAS Build.

```
<key>EXDefaultScreenOrientationMask</key>
<string>UIInterfaceOrientationMaskAllButUpsideDown</string>
```

However, having to manually add this configuration seems counter to the [prebuild strategy of using configuration plugins](https://docs.expo.dev/workflow/prebuild/#usage).

> This creates the android and ios directories for running your React code. If you modify the generated directories
> manually then you risk losing your changes the next time you run npx expo prebuild --clean. Instead, you should create
> config plugins — functions that perform modifications on native projects during prebuild.

This is especially problematic if you follow the [advice of adding `ios` and `android` to `.gitignore`](https://docs.expo.dev/workflow/prebuild/#clean).

> The purpose of the prompt is to encourage managed workflow users to
> `add the android and ios directories to the project's .gitignore`,
> ensuring that the project is always managed. However, this can make
> custom config plugins harder to develop so we  haven't introduced any
> mechanism to enforce this behavior.