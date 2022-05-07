# electron   

## electron's features

1. automatic updates    
2. Native menus & notifications.   
3. Crash reporting.    
4. Debugging & profiling.
5. Windows installers.
6. Just partial list.

## browser window params

```javascript
const mainWindow = new BrowserWindow({
  show:false,
  backgroundColor: "#FFF",
  width:800,
  height:600,
  minWidth:800,
  maxWidth:1024,
  minHeight:600,
  maxHeight:768,
  resizable:true,
  movable:true,
  alwaysOnTop:false,
  // frame: false, // to remove top title bar
  // titleBarStyle: 'hidden', // ??
  // transparent: true,
  title:'Sabarabamu Pawn'
})
```

## inter-process communication

Main-Process <--IPC--> Render Process

IPC async and IPC sync


## native dialog types  

1. file open   
2. file save   
3. message box   
4. error box    

dialog properties     

1. open file.
2. open Directory.
3. multiSelections.    
4. createDirectory.     
5. showHiddenFiles.    
6. promptToCreate(Windows Only)

## Message Box

1. info    
2. error    
3. question    
4. none    

## Webcontents Events

* before-input-event   
* certificate-error    
* context-menu    
* crashed     
* cursor-changed    
* destroyed    
* devtools-closed   
* devtools-focused   
* devtools-reload-page  etc  


## Debugging Electron Application  

1. chromium's dev tools   
2. VS Code's tools   
3. node-inspector   
4. testing with SPECTRON (unit test)  


## Building your application    

```bash
npm install electron-builder --save-dev   
```


## Configuring the Windows Installer   


## Auto updating

use autoUpdater from electron-updater instead of electron    

```bash
npm install electron-updater   
```

```javascript
autoUpdater.on('checking-for-update',()=>{})
autoUpdater.on('update-available',()=>{})
autoUpdater.on('update-not-available',()=>{})
autoUpdater.on('update-downloaded',()=>{})
autoUpdater.on('error',(event,error)=>{})
```


## to create installer

"electron-builder": "~22.10.5" version is working fine at the moment.    

```bash
npm install electron-builder --save-dev    
```

then go to package.json file

1. add "productName".
2. add "description" if you want.
3. create new script for builder in scripts.
4. add "build" Configuring.

```json
{
  "productName": "Application Name",
  "description": "My Electron application description",
  "scripts": {
    "--": "--",
    "build-installer": "electron-builder"
  },
  "build":{
    "appId": "Pawn Center",
    "win":{
      "target": ["nsis"],
      "icon": "icon_path.ico"
    },
    "nsis":{
      "installerIcon":"icon_path.ico",
      "uninstallerIcon":"icon_path.ico",
      "uninstallerDisplayName":"Application Name",
      "license":"license_text_file_path.txt",
      "oneClick": false,
      "allowToChangeInstallationDirectory": true
    }
  }
}
```


# NODE WEBKIT TUTORIAL    

init project   
```bash
npm i nw@0.44.1-sdk nw-builder -D
```

add some scripts   
```javascript
{
  "scripts":{
    "dev":"nw src/",
    "prod":"nwbuild --platforms win32,win64,linux32,linux64 --buildDir dist/ src/"
  }
}
```

creat src folder and
create another package.json file inside src folder
```bash
npm init
```


```json
{
  "window":{
    "title":"Breakout",
    "icon":"assents/icon.png",
    "toolbar": false,
    "width":1000,
    "height": 1000,
    "min_width":1000,
    "max-height":1000,
    "position":"mouse"    
  }
}
```
