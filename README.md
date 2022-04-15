
mkdir app
cd app

git init

npm init
//preciona enter para todas as opçoes
// no final vc terar um arquivo package.json
// para ver no terminal escreva dir

instalar 4 dependencia para inplementação
npm install typescript webpack webpack-cli ts-loader --save-dev
// sera adicionado uma pasta node_modules e um arquivo package-lock.json
// no arquivo package.json sera adicionado essas dependencias
  "devDependencies": {
    "ts-loader": "^9.2.8",
    "typescript": "^4.6.3",
    "webpack": "^5.72.0",
    "webpack-cli": "^4.9.2"
  }

adicione o arquivo 
.gitignore

para não ler o node_modules adicione essa restrição
node_modules/
dist/

para configura o typescript e orientar o compilador, executa isso no terminal
tsc --init
//vc tera um arquivo tsconfig.json
altere
"outDir": "./dist", 
"module": "es6",

adiciona um arquivo 
type nul > index.html
<html>
    <body>
        <h1>
            Hello World!!!
        </h1>
    </body>
</html>

adicione um pasta src
mkdir src

para criar um bundle
no arquivo package.json adicione
  "scripts": {
    "build":"webpack"
  },

crie um arquivo
webpack.config.js

adicione essas configuração 
const path = require('path');

module.exports = {
  entry: './src/index.ts',
  module: {
    rules: [
      {
        test: /\.tsx?$/,
        use: 'ts-loader',
        exclude: /node_modules/,
      },
    ],
  },
  resolve: {
    extensions: ['.tsx', '.ts', '.js'],
  },
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist'),
  },
};

link para maior informaçãp
https://webpack.js.org/guides/typescript/#root

crie um novo arquivo em src
type nul > ./src/index.ts

podemos executar webpack desta forma agora
npm run build

se aparecer isso, quer dizer que rodou com sucesso

> solid-with-typescript@1.0.0 build
> webpack

asset bundle.js 0 bytes [emitted] [minimized] (name: main)
./src/index.ts 15 bytes [built] [code generated]

WARNING in configuration
The 'mode' option has not been set, webpack will fallback to 'production' for this value.
Set 'mode' option to 'development' or 'production' to enable defaults for each environment.
You can also set it to 'none' to disable any default behavior. Learn more: https://webpack.js.org/configuration/mode/  

webpack 5.72.0 compiled with 1 warning in 20122 ms

agora vc tem um aquivo dentro do diretorio dist bundle.js

adicione isso no seu arquivo index.html
<html>
    <body>
        <h1>
            Hello World!!!
        </h1>
        <script src="./dist/bundle.js"></script>
    </body>
</html>

adicione a dependencia para executa no navegador um localhost
npm install http-server --save-dev

no arquivo package.json atualize o "scripts": {...} adicionado
"start": "http-server"

no seu terminal, executa
npm run start 


