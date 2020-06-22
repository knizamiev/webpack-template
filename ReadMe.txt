
mkdir react-template
cd react-template
mkdir -p src/components src/styles

npm init

npm install webpack webpack-cli --save-dev

npm install react react-dom --save

npm install @babel/core babel-loader @babel/preset-env @babel/preset-react --save-dev

npm install css-loader style-loader --save-dev

npm install html-webpack-plugin --save-dev


npm install webpack-dev-server --save-dev


file babelrc{
  "presets": ["@babel/preset-env", "@babel/preset-react"]
}

file webpack.config.js{
const path = require("path");
const HtmlWebpackPlugin = require("html-webpack-plugin");

module.exports = {
    entry: "./src/index.js",
    output: {
        path: path.join(__dirname, "/dist"),
        filename: "index-bundle.js"
    },
    module: {
        rules: [
            {
                test: /\.js$/,
                exclude: /node_modules/,
                use: ["babel-loader"]
            },
            {
                test: /\.css$/,
                use: ["style-loader", "css-loader"]
            },
            {
                test: /\.svg$/,
                loader: 'svg-inline-loader'
            }
        ]
    },
    devServer: {
        historyApiFallback: true,
        port: 9000

    },
    plugins: [
        new HtmlWebpackPlugin({
            template: "./src/index.html"
        })
    ]
};
}