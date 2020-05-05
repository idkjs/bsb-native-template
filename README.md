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

# Bsb Native Using Belt
## Code Seperation with Belt

If you add:
```re
let beltWorks = Belt.List.length([1, 2, 3]);
Js.Console.log(beltWorks);
```

to `index.re` and run `npm run build:web` you will see that you are good to go.

If you try to build `native` or `byte` the compiler will throw an error.

```sh
Error: Unbound module Belt
FAILED: subcommand failed.
```

## Further Study

1. [https://tech.ahrefs.com/how-to-write-a-library-for-bucklescript-and-native](https://tech.ahrefs.com/how-to-write-a-library-for-bucklescript-and-native-22f45e5e946d)

2. [bsansouci/matchenv](https://github.com/bsansouci/matchenv) [dead?](https://github.com/BuckleScript/bucklescript/pull/4219)

3. `Sys.argv` [BS_NATIVE](https://github.com/BuckleScript/bucklescript/blob/c861780650c9f093250cf7448f58e55f2ee86d1c/jscomp/main/bsb_main.ml#L83)

4. `Sys.argv` [BS_BROWSER](https://github.com/BuckleScript/bucklescript/blob/407d24b141bca40b5ff887ebd04cd0db438ba663/jscomp/stubs/bs_hash_stubs.ml#L2)

5. `Sys.argv` [BS_WATCH_CLEAR](https://github.com/BuckleScript/bucklescript/blob/7015ce12d629fd9b6385045e5b486f54a941d956/bsb#L425)

Usage: `"start": "BS_WATCH_CLEAR=true bsb -make-world -w",`

6. `Sys.argv` [BS_NATIVE_PPX](https://github.com/BuckleScript/bucklescript/blob/3989f0feee78827d548be0a0bc22dea607c3c5a9/jscomp/syntax/native_ast_derive_abstract.ml#L172)

7. [type backend_type](https://github.com/BuckleScript/bucklescript/blob/7015ce12d629fd9b6385045e5b486f54a941d956/jscomp/stdlib-406/sys.ml#L22)

```re
type backend_type =
  | Native
  | Bytecode
  | Other of string
```

8. `Sys.argv` [BS](https://github.com/BuckleScript/bucklescript/blob/7015ce12d629fd9b6385045e5b486f54a941d956/jscomp/stdlib-406/sys.ml#L40)

9. [`ocaml-dependencies`] not in  [`#build-schema.json`](https://bucklescript.github.io/bucklescript/docson/#build-schema.json). Its in [bsb-native here](https://github.com/bsansouci/bsb-native/blob/6410b9808ab7e1f6ec5c3cf8770c5d8b9182c3d6/lib/bsb_helper.ml#L5107) thanks to [@anmonteiro](https://discordapp.com/channels/235176658175262720/235200837608144898/707317419621875742).

## [Conditional compilation](https://github.com/bsansouci/bucklescript#conditional-compilation)

If you would like to have all your code in the same package, you can use BuckleScript's conditional compilation. To do so, place

```re
#if BSB_BACKEND = "bytecode" then
  include MyModule_Native
#elif BSB_BACKEND = "native" then
  include MyModule_Native
#else
  include MyModule_Js
#end

(* We support Darwin, Linux, Windows compile time checks *)
#if OS_TYPE = "Darwin" then 
  external fabs : float -> float = "fabs"
#end
```

Docs are old I think so...

```re
#if BS_BACKEND = "bytecode" then
  include MyModule_Native
#elif BS_BACKEND = "native" then
  include MyModule_Native
#else
  include MyModule_Js
#end

(* We support Darwin, Linux, Windows compile time checks *)
#if OS_TYPE = "Darwin" then 
  external fabs : float -> float = "fabs"
#end
```

Didn't work in [reason-cli-tools](https://github.com/idkjs/reason-cli-tools)
