# electron-python
This is a basic calculator app to calculate sum of two numbers using Eletron based GUI and using python based backend and connected using Zerorpc.

## Setting up the python environment

`````
pip install zerorpc
pip install pyinstaller
# for windows only
pip install pypiwin32 # for pyinstaller

`````

## Node.js /Electron Part

Configure the package.json

`````


  "name": "pretty-calculator",
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

clean the caches

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
To run 

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

Python - Run the following command

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

Running into errors after tring to updated the Node version to 8.2.1






