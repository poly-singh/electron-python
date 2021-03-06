# Electron-Python
This is a basic calculator app to calculate sum of two numbers using Electron based GUI and using python based backend connected using Zerorpc.

## Setting up the python environment

`````
Go to python.org ,and Download python 3.7.0 -to install python
pip install zerorpc
pip install pyinstaller
# for windows only
pip install pypiwin32 # for pyinstaller

`````
## Setting up the Electron and Frontend Environment

````
Go to repo https://github.com/coreybutler/nvm-windows/releases
Downlaod nvm-setup.zip and install it
nvm install 8.2.1 - # install node version 8.2.1
nvm use 8.2.1

`````


## Node.js /Electron Part

Configure the package.json

`````


  "name": "calculator",
  "main": "main.js",
  "scripts": {
    "start": "electron ."
  },
  "dependencies": {
    "zerorpc": "git+https://github.com/0rpc/zerorpc-node.git"
  },
  "devDependencies": {
    "electron": "^1.7.6",
    "electron-packager": "^9.0.1"
  }
}


`````

Clean the caches

`````
# On Window PowerShell (not cmd.exe!!!)
# clean caches, very important!!!!!
Remove-Item "$($env:USERPROFILE)\.node-gyp" -Force -Recurse -ErrorAction Ignore
Remove-Item "$($env:USERPROFILE)\.electron-gyp" -Force -Recurse -ErrorAction Ignore
Remove-Item .\node_modules -Force -Recurse -ErrorAction Ignore

`````

Run npm 

`````
npm install --runtime=electron --target=1.7.6

# verify the electron binary and its version by opening it
./node_modules/.bin/electron

`````
### To run 

`````
./node_modules/.bin/electron . 

`````

If some dynamic linking error shows up ,try to clean the caches and install the libraries again

`````
rm -rf node_modules
rm -rf ~/.node-gyp ~/.electron-gyp

npm install

`````

#### Packaging

## Python - Run the following command

`````
pyinstaller pycalc/api.py --distpath pycalcdist

rm -rf build/
rm -rf api.spec

`````
It it goes well older should show up, as well as the executable inside that folder. This is the complete independent Python executable that could be moved to somewhere else.

### Packaging the Electron application (with the python backend)

Make sure to use using Node 8.2.1

`````
./node_modules/.bin/electron-packager . --overwrite --ignore="pycalc$" --ignore="\.venv" 

`````

After successfully updating the node version 8.2.1 , packaged the application successfully

### Screenshot of the application

![calculator_image](./image/calculator_image.png)







