# Handlebars Static Loader
## Create static pages with your bundles
![](logo)
```JavaScript
const ExtractTextPlugin = require('extract-text-webpack-plugin');

module.exports = {
    module: {
        loaders: [
            {
                test: /\.hbs$/,
                loader: ExtractTextPlugin.extract([
                    'html-loader',
                    {
                        loader: 'handlebars-static-loader',
                        query: {
                            partials: './partials',
                            data: {name: 'Iddan'}
                        }
                    },
                ])
            }
        ]
    },
    plugins: [
        ExtractTextPlugin
    ],
    entry: './page.hbs',
    output: './page.html'
}
```

### API
#### Loader Query Properties

##### query.data
Data to pass to the handlebars template.

#### query.partials
Directory to load Handlebars Partials from (as in express's hbs view engine).

#### Todo

- Make the loader standalone without additional plugins and loaders.

### Compatibility
Tested on Webpack 2 beta on Node.js 6 LTS.

Should be compatible with Webpack 1 and any version of Node.js.

[logo]: assets/handlebars-static-loader.png "Logo Title Text 2"
