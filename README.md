# USMA-App
AlienVault USMA SIEM Mobile Application
## app.json
```json
{
  "expo": {
    "name": "TechmVault",
    "slug": "techm-vault",
    "version": "1.0.0",
    "orientation": "portrait",
    "icon": "./assets/icon.png",
    "userInterfaceStyle": "light",
    "splash": {
      "image": "./assets/splash.png",
      "resizeMode": "contain",
      "backgroundColor": "#ffffff"
    },
    "plugins": [
      [
        "expo-screen-orientation",
        {
          "initialOrientation": "LANDSCAPE_LEFT"
        }
      ]
    ],
    "assetBundlePatterns": [
      "**/*"
    ],
    "ios": {
      "requireFullScreen": true,
      "supportsTablet": true
    },
    "android": {
      "adaptiveIcon": {
        "foregroundImage": "./assets/adaptive-icon.png",
        "backgroundColor": "#ffffff"
      }
    },
    "web": {
      "favicon": "./assets/favicon.png"
    }
  }
}

```
## package.json
```json
{
  "name": "techmvault",
  "version": "1.0.0",
  "main": "node_modules/expo/AppEntry.js",
  "scripts": {
    "start": "expo start",
    "android": "expo start --android",
    "ios": "expo start --ios",
    "web": "expo start --web"
  },
  "dependencies": {
    "@expo/metro-runtime": "~3.1.3",
    "expo": "~50.0.14",
    "expo-screen-orientation": "~6.4.1",
    "expo-status-bar": "~1.11.1",
    "react": "18.2.0",
    "react-dom": "18.2.0",
    "react-native": "0.73.6",
    "react-native-web": "~0.19.6",
    "react-native-webview": "13.6.4",
    "react-native-safe-area-context": "4.8.2"
  },
  "devDependencies": {
    "@babel/core": "^7.20.0"
  },
  "private": true
}
```

## App.js
```javascript
import React, { useEffect } from 'react';
import { StyleSheet } from 'react-native';
import { WebView } from 'react-native-webview';
import * as ScreenOrientation from 'expo-screen-orientation';
import { SafeAreaProvider, SafeAreaView } from 'react-native-safe-area-context';

export default function App() {
  useEffect(() => {
    const unlockScreenOrientation = async () => {
      try {
        await ScreenOrientation.unlockAsync();
      } catch (error) {
        console.error('Failed to unlock screen orientation:', error);
      }
    };

    unlockScreenOrientation();

    return async () => {
      await ScreenOrientation.lockAsync(ScreenOrientation.OrientationLock.LANDSCAPE_LEFT);
    };
  }, []);

  return (
    <SafeAreaProvider>
      <SafeAreaView style={styles.container}>
        <WebView source={{ uri: 'https://reactnative.dev/' }} style={{ flex: 1 }} />
      </SafeAreaView>
    </SafeAreaProvider>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#000',
  },
});

```
