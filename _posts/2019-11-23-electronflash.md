---
layout: post
title: 'Electron에서 Flash 사용방법과 블랙스크린이 나타나는 문제 해결방법'
author: BearKim
date: 2019-11-23 00:25
tags: [electron, flashplayer]
---

글을 너무 안쓴지 오래되서 뭐라도 쓰고싶었는데, 이 이슈가지고 낭비한 세시간이 너무 안타까워서 짤막한 글 몇 줄 남기기로 하였다.

구시대 유물이지만 아직도 Flash는 간간히 쓰이고 있다. 최근 프로젝트에서 Electron에 WebView로 웹페이지를 열고, 이 안에 Flash컨트롤러를 활성시킬일이 있는데 문제는 까만화면이 뜨면서 아무것도 먹질않는 것이다. 이 때문에 애꿎은 FlashPlayer버전과 윈도우 32비트 64비트, 혹은 리눅스에서 빌드하며 속만 타들어가다가 깃헙 이슈를 발견하였다.<br> 바로 그 문제의 원인은 Electron 버전이었다. **Electron 버전이 5 이상의 버전에서는 Flash가 정상적으로 동작하지 않는다**는 것이었고, 이에 구버전의 Electron을 사용해야만 정상적으로 동작이 가능하다는 것이었다. 여기서 추천하는 버전은 **4.2.11**이었다. 해당 버전으로 실행을 해본결과, 낭비한 세시간이 무색하게 너무 잘 동작하였다.
<br>
Electron에서 FlashPlayer를 불러오는 소스는 너무 쉽게 검색이 가능하므로, Electron Officiala 문서 링크로 대체한다.
<br>
[Electron Flash 사용하기](https://tinydew4.github.io/electron-ko/docs/tutorial/using-pepper-flash-plugin/)
<br>
참고로 빌드에 사용한 package파일 하나 첨부하고 글을 마치겠다.
```json
{
  "name": "dk-electron",
  "version": "1.0.0",
  "description": "dk electron wrapping",
  "main": "main.js",
  "scripts": {
    "start": "electron . --development=true",
    "build:osx": "electron-builder --mac",
    "build:linux": "npm run build:linux32 && npm run build:linux64",
    "build:linux32": "electron-builder --linux --ia32",
    "build:linux64": "electron-builder --linux --x64",
    "build:win": "npm run build:win32 && npm run build:win64",
    "build:win32": "electron-builder --win --ia32",
    "build:win64": "electron-builder --win --x64"
  },
  "author": "bearkim",
  "devDependencies": {
    "asar": "^2.0.1",
    "electron": "^4.2.11",
    "electron-builder": "^21.2.0"
  },
  "dependencies": {
    "macaddress": "^0.2.9",
    "nw-flash-trust": "^0.3.0",
    "url": "^0.11.0",
    "yargs": "^14.2.0"
  },
  "build": {
    "productName": "DkElectron",
    "appId": "net.dkant.dkelectron",
    "asar": false,
    "protocols": {
      "name": "dk-electron",
      "schemes": [
        "dkelectron"
      ]
    },
    "extraResources": [
      {
        "from": "./extraResources/",
        "to": "extraResources",
        "filter": [
          "**/*"
        ]
      }
    ],
    "mac": {
      "target": [
        "default"
      ],
      "icon": "./resources/installer/Icon.icns"
    },
    "dmg": {
      "title": "HelloElectron",
      "icon": "./resources/installer/Icon.icns"
    },
    "win": {
      "target": [
        "zip",
        "nsis"
      ],
      "icon": "icons/icon.ico"
    },
    "linux": {
      "target": [
        "AppImage",
        "deb",
        "rpm",
        "zip",
        "tar.gz"
      ],
      "icon": "./resources/linuxicon"
    },
    "nsis": {
      "oneClick": false,
      "allowToChangeInstallationDirectory": true
    },
    "directories": {
      "buildResources": "resources/installer/",
      "output": "dist/",
      "app": "."
    }
  }
}

```