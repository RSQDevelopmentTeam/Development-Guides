NOTES

NEED TO BE RUNNING NODE V16

use: ['runs Last',‘runs Second’,'runs First']

test: What files are we looking for add a express like I.E /\.(sa|sc|c)ss$/,

clean: true means it clears out the out put files in order to put knew ones in.

devtool: 'source-map', Choose a style of source mapping to enhance the debugging process. These values can affect build and rebuild speed dramatically.

MiniCssExtractPlugin.loader, creates a css file

css-loader, interprets @import and url() like import/require() and will resolve them.

"postcss-loader", run plugins you want via the postcss.congif.js (Nanocss (Removes unsed css) and autoprefix(provides support for all browsers))

"sass-loader", turns scss to css

MiniCssExtractPlugin

This plugin extracts CSS into separate files. It creates a CSS file per JS file which contains CSS. It supports On-Demand-Loading of CSS and SourceMaps.



