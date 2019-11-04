# repro-prettier-editorconfig

This repo shows how .editorconfig settings will override prettier's unset defaults, even when a prettier config file exists.

# Getting started

```
yarn
```

Run prettier with 

```
yarn prettier --write src/**/*.js
```

# Results

**Expected results**

* File `src/tabWidth4/index.js` should be formatted with 4 spaces as per the nearest `prettier.config.js` ✔️
* File `src/tabWidthDefault2/index.js` should be formatted with 2 spaces as it is left unset in the nearest `prettier.config.js` ❌

**Actual results**

File `src/tabWidthDefault2/index.js` is actually formatted with 16 spaces as per `.editorconfig`. What is perhpas most unsettling is that a `.editorconfig` file might not even be part of this repo: any `.editorconfig` found further up the tree strcture, **even when outside this project**, will affect prettier's behavior.