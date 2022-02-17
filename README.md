# Tips

## Unity

- Set an `Application.targetFrameRate` because it can sometimes default to 30 and make a game feel bad, even on more powerful devices
- You probably want to set `Screen.sleepTimeout = SleepTimeout.NeverSleep` because the default inactive sleep time can be very short on some devices
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

# or if you've got JAVA_HOME set up using a Unity Android player:
"$JAVA_HOME/../SDK/platform-tools/adb.exe" logcat -s Unity
```

### WebGL

- "File"/other persistent changes are synced to the browser's indexed DB, but (by default) only when Unity internally thinks it should sync it. This means you can successfully write a file, and then exit the application, and that write can be lost.
    - See [this StackOverflow Q&A for a solution](https://gamedev.stackexchange.com/questions/184369/file-saved-to-indexeddb-lost-unless-we-change-scenes)
    - This has also been solved in [MyLibrary.KVS](https://github.com/bilalakil/my-unity-library/commit/7c1bd6c691cc201115b3ce9c244a8a8ee0b27564)

### Other

- If using CloudOnce:
    - When installing for the first time, be sure to switch to the PC platform to avoid a `GooglePlayServices` missing exception. From there, you can update the External Dependency Manager (at the bottom of the Assets menu) and then switch to Android.
    - The External Dependency Manager seems to ignore the Android SDK that's linked to Unity's preferences, and uses `JAVA_HOME` instead.
    - Changes to `JAVA_HOME` aren't picked up by the External Dependency Manager even after restarting Unity. I restarted my entire PC for this to work. 

## Useful Resources

- [Good intro to Git](https://www.youtube.com/watch?v=C1wuPNcmdhQ)
