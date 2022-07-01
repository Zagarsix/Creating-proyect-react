## 1.- iniciar el proyecto con npm

$npm init -y

## 2.- Crear nuestra estructura de carpetas y archivos

public     index.html
src    index js
.babellrc
.gitignore
readme.md
webpack.config.js

## 3.- instalar webpack

$ npm i --save-dev webpack webpack-dev-server webpack-cli

## 4.- configurar webapck en nuestro package.json

{
    ...
    "scripts":{
        "build": "webpack --mode production",
        "test": "echo"\"error: etc
    }
}

## 5.- Configurar el archivo webpack.config.js

const path= require('path');

module.exports = {
    entry: path.resolve(__dirname, './src/index.js'),
    output: {
        path: path.resolve(__dirname, './dist'),
        filename: 'bundle.js'
    }
}

## 6.- Modificar el archivo package.json y agregar el comando "start"

{
    ...
    "scripts":{
        "start": "webpack serve --config ./webpack.config.js --mode development"
        "build": "webpack",
        "test": "echo"\"error: etc
    }
}

## 7.- Modificar nuestro archivo index.html con la siguiente estructura:

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
    </head>
    <body>
        
    </body>
    </html>

## 8.- Instalar html-webpack-plugin para vincular nuestro index.html con nuestro archivo.js

    $ npm i --save-dev html-webpack-plugin

## 9.- Configurar nuestro webpack.config.js con html-webpack-plugin

const HtmlWepackPlugin = require('html-webpack.plugin');

module.exports = {
    ...
    plugins: [
        new HtmlWepackPlugin({
                template: path.resolve(__dirname, './public/index.html'),
                filename: 'index.html'
        })
    ]
}

## 10.- Configurar nuestro dev server en el webpack.config.js

    module.exports = {

        ...
        dev Server: {
            port: 3000,
            hot: true,
            compress: true,
            allowedHosts: ['all']
        }
            ...
    }

## 11.- Instalar babel para portabilidad de javascript

    $ npm i --save-dev @babel/core @babel/presetr-env babel-loader

## 12.- Modificar el archivo .babelrc y agregar el siguiente código:

    {
        "presets": [
            "@babel/preset-env"
        ]
    }

## 13.- Modificar el archivo webpack.config.js y agregar las reglas para babel

    module.exports = {
        ...
        module: {
            rules: [
                {
                    test: /\.(js|jsx)$/,
                    exclude: /node_modules/,
                    use: ['babel-loader']
                }
            ]
        }
    }

## 14.- Instalar react y react-dom 18 con babel

    $ npm i --save-dev @babel/preset-react
    $ npm i --save react react-dom

## 15.- Modificar el archivo .babelrc para añadir react

    {
        "presets": [
            "@babel/preset-react"
        ]
    }

## 16.- Añadir extensiones en el webpack.config.js para trabajar con react

    module.exports = {
        ...
        resolve: {
            exstensiones: ['*', '.js', '.jsx']
        }
    }

## 17.- Añadir al archivo Index.html el contenedor donde se renderizará todo nuestro contenido de react

    ...
    <body>
        <div id="root"></div>
    </body>
    ...

## 18.- Configurar nuestro index.js para trabajar con react

    import React from 'react';
    import reactDOM from 'react-dom/client';

    const App = () => {
        return (
            <h1>App React 18</h1>
        )
    }

    const root = document.querySelector('#root');
    ReactDOM.createRoot(root).render(<App />);

## 19.- Instalar compatibilidad con css y sass

    $ npm i --save-dev mini-css-extract-plugin sass sass-loader css-loader

## 20.- Configurar webpack.config.js para trabajar con css(sass)

    const MiniCssExtractPlugin = require('mini-css-extract-plugin');

    module: {
        rules: [
            ...
            {
                test: /\.(css|scss)$/i,
                use: [MiniCssExtractPlugin.loader, 'css-loader', 'sass-loader']
            },
            ...
        ],
        ...
        plugins: [
            ...
            new MiniCssextractPlugin({
                filename: 'style.css'
            }),
            ...
        ]
    },

## 21.- Añadir archivo css e importarlo en nuestro archivo index.js

    - Contenido Archivo index.css
    ... 
    body {
        background-color: aquamarine;
    }
    ...

     - Contenido Archivo index.js
    ... 
    import './index.css';
    ...

    ___________________________________

    - Contenido Archivo index.css
    ... 
    body {
        background-color: aquamarine;
    }
    ...

     - Contenido Archivo index.js
    ... 
    import './index.scss';
    ...

## 22.- Instalar bootstrap (opcional)

    $ npm i --save bootstrap @popperjs/core

## 23.- Añadir bootstrap a nuestro proyecto en el index.js

    ...
    import 'bootstrap/dist/css/bootstrap.min.css';
    import '@popperjs/core';
    import 'bootstrap/dist/js/bootstrap.bundle';
    ...