In this sample we are going to start working with css in hmr modules

We will start from sample 01 Update module js

First let's install both loaders with the following command:

```npm install --save-dev style-loader css-loader```

Now in the webpack.config.js let's update the configuration file to make use of the loader.

```javascript
    module: {
        rules: [
          {
            test: /\.css$/,
            use: ['style-loader', 'css-loader'],
          },
        ],
    },
```

Create the styles.css

```css
body {
    background: aquamarine;
}
```

Import the file in app.js

```webpack
import './styles.css';
```

And add style for the text

```javascript
divComponent.classList.add('text-color');
```

```css
.text-color {
    color: red;
}

body{
    background-color: blue;
}
```

Now we can change de color to blue and the background-color to red 
the changes will be updated without lost the input focus


