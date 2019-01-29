# ocasta-react-scripts

This package includes custom scripts and configuration used by [Create React App](https://github.com/facebook/create-react-app).

Our changes:
- allow absolute path imports by providing an alias to /src as AppSrc
- also expose AppSrc alias to eslint and jest
- eslint in webpack takes any custom config: put your custom .eslintrc. in the root folder of your starter app. In order for it to see AppSrc alias, you may need to use .eslintrc.js instead so you can import paths from it, without this eslint thinks they are unresolved imports:

	const path = require('path');

  'settings': {
    'import/resolver':  {
      alias: {
        map: [
         ['AppSrc', path.resolve(__dirname, './src')],
        ]
      },
      'webpack': {
        'config': './node_modules/ocasta-react-scripts/config/webpack.config.js'
      }
    }
  },

- remove facebook's custom formatting of the webpack console output and put back the default more verbose one. The reason for that is Facebook only showed linting errors for the last processed file so you  were forced to fix files in a specific order with no clue how long it would take to get your code up to scratch. The default webpack output shows everything that is wrong with all the files so it is more helpful to the developer: you can evaluate workload and fix errrors in order of convenience.
- change typescript definitions path to our module ocasta-react-scrtipts

To make a starter app with create-react-app and this customised config, please run:

npx create-react-app test-app --scripts-version ocasta-react-scripts

Please refer to its documentation:

- [Getting Started](https://facebook.github.io/create-react-app/docs/getting-started) – How to create a new app.
- [User Guide](https://facebook.github.io/create-react-app/) – How to develop apps bootstrapped with Create React App.
