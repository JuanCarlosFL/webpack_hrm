The Most Easy example with HMR (Hot Module Replacement)

Init the project

```npm init -y```

Install webpack, webpack dev server and html webpack plugin

```npm i -D webpack webpack-cli webpack-dev-server html-webpack-plugin```

In the package.json create this script

```"start:dev": "webpack serve --mode development"```

And now create the file webpack.config.js with this configuration,
very important to add in the dev server configuration the property hot to true

```
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
    entry: path.resolve(__dirname, 'src', 'app.js'),
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'bundle.js'
    },

    plugins: [
        new HtmlWebpackPlugin({
            title: "Webpack dev server"
        })
    ],
    devServer: {
        port: 8085,
        contentBase: './dist',
        hot:true
    }
}
```

In the principal file (app.js) we have add this.
When a change inside div.js is detected we tell webpack to accept the updated module

```
if (module.hot){
    module.hot.accept('./components/div.js', () =>{
        const newComponent = DIV();
        document.body.replaceChild(newComponent, divComponent);

        divComponent = newComponent;
    })
}
```

now start running the script and in the browser go to localhost:8085

For test if is working we can write in the input text and change the text in div.js when we save the changes the text will be updated and don't loose the input focus
