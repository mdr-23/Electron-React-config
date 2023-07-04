# Electron App with React

This is a template for creating Electron applications with React.

## Installation and Configuration

Follow these steps to install and run the Electron app:

1. Install Electron as a development dependency:
```bash
npm install electron --save-dev
```

2. Create a new file named electron.js in the root of your project. In this example, it will be created in the src folder:

3. Add the following code to electron.js:
```javascript
const { app, BrowserWindow } = require('electron');

function createWindow() {
  const win = new BrowserWindow({
    width: 800,
    height: 600,
  });

  win.loadURL('http://localhost:3000');
}

app.whenReady().then(() => {
  createWindow();

  app.on('activate', function () {
    if (BrowserWindow.getAllWindows().length === 0) createWindow();
  });
});

app.on('window-all-closed', function () {
  if (process.platform !== 'darwin') app.quit();
});
```

4. To run your React application with Electron, add the following script to your package.json:
```json
"scripts": {
  "start": "react-scripts start",
  "electron ./src/electron.js",
}
```

5. Run the following command. This will build your React application and launch an Electron window displaying the application's user interface:
```bash
npm run electron
```
