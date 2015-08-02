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

## Usage

### Task:

```js
grunt.initConfig({
    svg_fallback: {
        your_target: {
            cwd: "cwd/", // <--- Folder with sources and results
            src: "sources/", // <--- Subfolders will be processed too
            dest: "result/" // <--- All processed folders wiil be placed here
        }
    }
});
```

### Configure with json:

Create **config.json** and place it to the folder with your SVG-images.

Variations of **config.json** see below:

#### Colorize:

For transparent images only!

If SVG-element has fills, these fills will not be replaced.

```js
{
    "defaultColor": "hotpink"
}
```

#### Resize and colorize images (without renaming):

```js
{
    "defaults": {
        "arrow-up": {
            "width": "200" // <--- height will be setted automatically
        },
        "home": {
            "height": "50", // <--- width will be setted automatically
            "color": "skyblue" //  <--- this override 'defaultColor'
        }
    }
}
```

#### Make variations of one file:

```js
{
    "variations": {
        "arrow-up": [{
              "width": "40" // ---> arrow-up--w40.svg
            }, {
              "height": "120",
              "color": "orange" // ---> arrow-up--h120--orange.svg
            }, {
              "color": "gold" // ---> arrow-up--gold.svg
        }],
        "home": [{
              "width": "100" // ---> home--w100.svg
            }, {
              "height": "70",
              "color": "pink" // home--h100--pink.svg
            }, {
              "color": "yellowgreen" // ---> home--yellowgreen.svg
        }]
    }
}
```

#### Combo (all modifications in one file):

```js
{
    "defaultColor": "blue", // <--- Set color

    "defaults": { // <--- 1. Defaults will be processed first
        "home": {
            "width": "123"
        },
        "remove": {
            "height": "32",
            "color": "teal"
        }
    },

    "variations": { // <--- 2. Then will be processed variations
        "arrow-up": [{
                "width": "40"
            }, {
                "width": "120",
                "color": "gold"
            }, {
                "color": "yellow"
        }],
        "home": [{
                "width": "100"
            }, {
                "width": "70",
                "color": "crimson"
            }, {
                "width": "20",
                "color": "gray"
            }, {
                "color": "green"
        }]
    }
}
```

## Release History

0.0.4 - Now fill color correctly overrides by config
