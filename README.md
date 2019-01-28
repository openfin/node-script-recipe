# OpenFin Node.js Recipe

Node.js Recipe demonstrating basic OpenFin build integration, creating a script that: 

* Creates an OpenFin configuration file
* Updates that configuration file with new values
* Downloads the OpenFin Runtime
* Launches the application

```js
var openfinConfigBuilder = require('openfin-config-builder'),
    openfinLauncher = require('openfin-launcher'),
    path = require('path');
 
function createConfig() {
    return openfinConfigBuilder.create({
            startup_app: {
                name: 'myApp',
                url: 'http://openfin.co'
            }
        }, 'app.json');
}
 
function updateConfig() {
    return openfinConfigBuilder.update({
            startup_app: {
                name: 'staging_app'
            }
        }, 'app.json');
}

function launchOpenfin () {
    return openfinLauncher.launchOpenFin({
            configPath: 'file:/' + path.resolve('app.json')
        });
}

//Create the OpenFin Configuration and then run the Application.
createConfig()
        .then(updateConfig)
        .then(launchOpenfin);
```

### Running the recipe:

```sh
$ git clone https://github.com/openfin/node-script-recipe.git

$ cd node-script-recipe

$ npm install

$ node index.js
```
## License
MIT

The code in this repository is covered by the included license.  If you run this code, it may call on the OpenFin RVM or OpenFin Runtime, which are subject to OpenFin’s [Developer License](https://openfin.co/developer-agreement/). If you have questions, please contact support@openfin.co”

## Support
Please enter an issue in the repo for any questions or problems. Alternatively, please contact us at support@openfin.co 
