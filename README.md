# Tips

## Unity

### iOS

- Check "Bottom" in "Project Settings > Player > iOS > Other Settings > Defer system gestures on edges"
    - Otherwise the home indicator on some iPhones will be too easy to activate

### Android

- Disable "Project Settings > Player > Android > Resolution and Presentation > Render Over Native UI"
    - Otherwise some devices will have their OS visible behind the game
- Debug logging on Windows (with git bash):
    - You'll probably need to change the editor version

```bash
cd /c/Program Files/Unity/Hub/Editor/2020.2.1f1/Editor/Data/PlaybackEngines/AndroidPlayer/SDK/platform-tools
./adb.exe logcat -s Unity
```
