# carousel

Создайте новую папку carousel, перейдите в неё и используйте npm init --yes для создания npm-проекта, то есть для генерации дефолтного файла package.json, в котором перечислены все зависимости (то есть используемые npm-пакеты) этого проекта.

Дальше откроем наш проект с помощью IDE или редактора кода и создадим небольшую структуру проекта, то есть папку src, а в ней файлы index.html и index.js. 

Напомним, что Webpack является библиотекой для Node.js. Он есть в npm, поэтому мы можем установить его с помощью команды npm i -D webpack.

Флаг -D — это сокращённо --save-dev. Он нужен, чтобы указать, что сам Webpack не попадёт в проект и не будет использоваться в браузере у конечного пользователя нашего приложения, то есть это development dependency, которая используется только для сборки.

Также нам понадобится npm i -D webpack-dev-server webpack-cli, чтобы запустить наше приложение и посмотреть, работает ли оно.

Теперь создадим в корне проекта файл webpack.config.js и скопируем из документации Webpack простейший конфиг для dev-server'а:

```js
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const { CleanWebpackPlugin } = require('clean-webpack-plugin');

module.exports = {
  mode: 'development',
  entry: {
    app: './src/index.js',
  },
  devtool: 'inline-source-map',
  devServer: {
    contentBase: './dist',
  },
  plugins: [
    new CleanWebpackPlugin(),
    new HtmlWebpackPlugin({
      template: 'src/index.html',
    }),
  ],
  output: {
    filename: '[name].bundle.js',
    path: path.resolve(__dirname, 'dist'),
  },
};
```

И установим ещё парочку плагинов для его работоспособности. 

npm i -D html-webpack-plugin clean-webpack-plugin

Устанавливаем flickity через npm, для этого находим страницу библиотеки в поиске npm.

И находим в разделе Install команду для установки:

npm i flickity
Обратите внимание, что флаг -D писать не надо, так как эта библиотека попадёт к пользователю, то есть она является обычной dependency.

Устанавливаем style-loader и css-loader:

npm install -D style-loader css-loader

Добавляем импорт CSS в index.js:
