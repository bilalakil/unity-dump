# Tips

## Unity

- Use TextMeshPro instead of the legacy Text components
    - Each time you update the TextMeshPro package, you should also re-import the TMPro Essentials.
    - Although re-import supposedly works on top of existing files, I've encountered issues with that before (where files were split into different folders and lookups failed). Instead, delete the current essentials and do a clean import.

### iOS

- Check "Bottom" in "Project Settings > Player > iOS > Other Settings > Defer system gestures on edges"
    - Otherwise the home indicator on some iPhones will be too easy to activate
    - Counter-intuitively, you must leave the "Hide home button on iPhone X" option unchecked, as this enables a different (undersired) behaviour, where the home indicator isn't visible until touched, but then still too easy to activate (in spite of the "Defer system gestures on edges" setting)

### Android

- Disable "Project Settings > Player > Android > Resolution and Presentation > Render Over Native UI"
    - Otherwise some devices will have their OS visible behind the game
- Debug logging on Windows (with git bash):
    - You'll probably need to change the editor version

```bash
cd "/c/Program Files/Unity/Hub/Editor/2020.2.1f1/Editor/Data/PlaybackEngines/AndroidPlayer/SDK/platform-tools"
./adb.exe logcat -s Unity
```

### Other

- If using CloudOnce:
    - When installing for the first time, be sure to switch to the PC platform to avoid a `GooglePlayServices` missing exception. From there, you can update the External Dependency Manager (at the bottom of the Assets menu) and then switch to Android.
    - The External Dependency Manager seems to ignore the Android SDK that's linked to Unity's preferences, and uses `JAVA_HOME` instead.
    - Changes to `JAVA_HOME` aren't picked up by the External Dependency Manager even after restarting Unity. I restarted my entire PC for this to work. 
