* npm install --save react react-dom react-router-dom
* npm install --save-dev webpack webpack-dev-server
* npm install --save-dev babel-loader babel-core babel-preset-react babel-preset-env
* npm install --save-dev css-loader style-loader
#
* in `webpack.config.js` set up the development workflow
#
* Webpack Docs: https://webpack.js.org/concepts/
* More about Babel: https://babeljs.io/
## Adding Babel-polyfill
The current setup won't support all browsers theoretically supported by React. Features like Promises and Object.assign()  are missing in older browsers - especially in IE of course.

If you need to support these browsers, you need to add a polyfill (a package which provides these features for older browsers). babel-polyfill  is a great and easy-to-use choice.

Add it like this:

npm install --save babel-polyfill 

Add the following import to the top of your index.js file:

import 'babel-polyfill';
Change the config of your env  babel preset in the .babelrc  file: 
```
"presets": [
    ["env", {
        "targets": {
            "browsers": [
                "> 1%",
                "last 2 versions"
            ]
        },
        "useBuiltIns": "entry"
     }],
     "stage-2",
     "react"
 ],
 ```
useBuiltIns  was added and by setting it to 'entry' , the import in the index.js  file (import 'babel-polyfill' ) is actually changed to import whatever features need to be supported for your chosen browsers and environment. More information can be found here: https://github.com/babel/babel-preset-env#usebuiltins-entry