# Bsb Native Template
---
This is a template for starting a [bsb-native](https://github.com/bsansouci/bucklescript) project.

`bsb-native` let's you generate [reason native](https://reason-native.com) code with [bucklescript](https://bucklescript.github.io).

It based on [Schmavery/ludum-dare-46](https://github.com/Schmavery/ludum-dare-46) which you should check out for an example using [Reprocessing](https://github.com/schmavery/reprocessing).

### Using the Template

Click the template button to generate a template:

[![use-this-template-button-image](./usethistemplate.png)](https://github.com/idkjs/bsb-native-template/generate)

or 

```
git clone https://github.com/idkjs/bsb-native-template.git
```

### Build Bytecode
```
npm install
npm run build
# start the project
npm start
```

### Build Native 

Same steps and out put as above because it doesn't matter for this template..

```
npm install
npm run build:native

# start the project
npm start:native
```

### Build Web 

```
npm run build:web

# start the project
npm start:web
```

To build to JS run `npm run build:web` which will run a a static server with [`serve`](https://www.npmjs.com/package/serve) and go to `http://localhost:5000`. If you're using safari you can simply open the `index.html` and tick `Develop > Disable Cross-Origin Restrictions`.

Check the browser console:
```sh
It Works
```

To build to native run `npm run build:native` and run `npm run start:native`. You should see:

```sh
~/Github/bsb-native-template master*
❯ npm run start:native

> bsb-native-template@ start:native /Users/mandalarian/Github/bsb-native-template
> ./index.exe

It Works
```
