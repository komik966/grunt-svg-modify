# grunt-svg-modify

This fork is quick modified version for my own purposes but you may find it useful.
I eliminated the need of config.json, instead configuration of svg transformations is defined in Gruntfile as options:
```js
svg_modify: {
    android: {
        src: 'icons/',
        dest: 'android/',
        options:{
            colors:[
                "ffebee","ffcdd2","ef9a9a","e57373","ef5350","f44336","e53935","d32f2f","c62828"
            ],
            sizes: [300]
        }
    }
}
```

> Resize and color svg-images

Modify SVG by JSON.

## Getting Started
This plugin requires Grunt `~0.4.5`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-svg-modify --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-svg-modify');
```
## Release History

0.0.4 - Now fill color correctly overrides by config
