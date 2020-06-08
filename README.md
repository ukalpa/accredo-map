#accredo-map

"accredo-map" is a tool of generating [accredo](https://www.npmjs.com/package/accredo) related endpoints, functions and actions so developers can bind it into [accredo](https://www.npmjs.com/package/accredo) for accessing Accredo data, for more information about the accredo package, please refer: http://github.com/ukalpa/accredo

 
Please notice: normally you don't need to install it, just execute it by 'npx' command to generate the mapping library:
```bash
npx accredo-map --url="http://localhost:6567/saturn/odata4/v1/company('demo')"
npx accredo-map --file="./source/metadata.xml" --company="test"
```

##Installation

```bash
$npm i accredo-map
```

##Generate Mapping Library

There are two types of generating map files, either you can import from a remote $metadata url or the local $metadata file

#### Generate mapping files according to the remote url
```bash
node dist/accredo-map.js --url="http://localhost:6567/saturn/odata4/v1/company('demo')/"
``` 

#### Generate mapping files according to the local file
```bash
node dist/accredo-map.js --file="./source/metadata.xml" --company="test"
```

After executing one of the above commands, the script will generate a new folder with mapping files in the directory "accredo-map"

## Parameters

By Url
```bash
--url="http://localhost:6567/saturn/odata4/v1/company('demo')/"
```

By File
```bash
--file="./source/metadata.xml" --company="test"
```

Optional, Set Destination Directory, "accredo-map" is the default value.
```
--dest="./test"
```

Optional, Set script files syntax, you can set "es5" or "es6", "es5" is the default value.
```
--es=es5
```
--es=es5/es6, es5 syntax as default

## Usage

- After executing one of the above commands, the generator will generate the related javascript files to "accredo-map/demo/*"
- Import it to the accredo instance in your code as below, then you should be able to call all entities, functions and actions

```javascript
const Accredo = require('accredo').default;
const accredo = new Accredo("http://localhost:6567/saturn/odata4/v1/company('demo')/");
require('./accredo-map/demo')(accredo);

// Start using at here:
accredo.ARCustomer.find("DEMO_CUSTOMER").then(function(customer){
    console.log("Got the customer:", customer, "plain object:", customer.toJSON());
})
```

For more information and commercial support, welcome to contact admin@bizex.co.nz
