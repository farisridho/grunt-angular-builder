## grunt-angular-build-tool

> A build tool for AngularJS applications.

<br>
To find out more about this project, read the [Introduction](https://github.com/claudio-silva/grunt-angular-build-tool/wiki/Introduction) page.

### 12 Features at a glance

Wouldn't it be great if there was a build tool that could:  
_(check all that apply to your needs)_

1. Analyze your AngularJS source code and "understand" the relationships between all your files?

- Accept source code split into as many files as you want and spread over any directory structure you prefer?

- Assemble one javascript file (or just a few) for production with all code assembled in the correct loading order required by your module's dependencies?

- Generate ultra-fast debug builds that make your browser load the original source files in the correct order (no need to minify and concatenate files during debug)?

- Allow you to debug the source code in the browser itself and see readable source code for any debug breakpoint or error location, with the correct original line numbers?

- Include in your build _only_ the modules that your app actually needs and discard dead code?

- Automatically include all stylesheets and assets required by each module?

- Also include in the build non-AngularJS standalone scripts?

- Recognize modules and libraries that are loaded independently and, therefore, are not part of the build?

- Not only build complete applications but also build library projects, generating _readable_ redistributable source code files for them?

- Allow fine-tuning the build process with optional configuration files present on some source folders?

- Integrate easily with other Grunt plugins to expand your build process with minification, optimization, preprocessing and/or compilation steps?

If you checked more than one option, this tool might just be the one you were looking for!

How about giving it a try on your next project?

---

### Roadmap

1. ~~Javascript builder.~~ [done]
1. Per directory build-config files support.
1. CSS builder.
2. Assets builder.

**The project is under active development.** More functionality will be available very soon.

---

# Documentation

Extended documentation is available on the [Wiki](https://github.com/claudio-silva/grunt-angular-build-tool/wiki).

## Getting Started

> This plugin is available for installation from **npm**.

>**Do not donwload the source code from the git repository into your project**, for you could end up using a (possibly) very unstable development version and **not a stable release**.

Start by installing Grunt `~0.4.1` on your project.

If you haven't used [Grunt](http://gruntjs.com) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins.

Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-angular-build-tool --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-angular-build-tool');
```

## The "angular-build-tool" task

### Overview
In your project's Gruntfile, add a section named `angular-build-tool` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  'angular-build-tool': {
    options: {
      // Task-specific options go here.
    },
    your_target: {
      // Target-specific file lists and/or options go here.
    },
  },
})
```

The available options are explained in the [Configuring tasks](https://github.com/claudio-silva/grunt-angular-build-tool/wiki/Configuring-tasks) page.

### Basic Use

This is the minimal recommended `Gruntfile.js`.

```js
module.exports = function (grunt)
{
  grunt.initConfig ({

    'angular-build-tool': {
      options: {
        main: 'mainModuleName'
      },
      app: {
        src:          'src/**/*.js',
        targetScript: 'build/project.js'
      }
    }

  });
  
  grunt.loadNpmTasks ('grunt-angular-build-tool');
  
  grunt.registerTask ('release', ['angular-build-tool']);
  grunt.registerTask ('debug', ['angular-build-tool::debug']);

};
```

### Running tasks

To run the above task:

- For a releast build, type `grunt angular-build-tool` on the command line;
- For a debug build, type either:
    - `grunt angular-build-tool::debug`, or
    - `grunt angular-build-tool --build=debug`.

If you define your own alias tasks with more complex build steps, run `grunt your-task-name` instead.

> Tip: you can use the `--build=debug` option to convert any task alias into a _debug_ build (assuming it includes an angular-build-tool subtask).

### The recommended tasks alias

The example above includes two alias tasks registered at the bottom. These tasks are customizable shortcuts to your build process. They are a starting point for you to expand with additional subtasks provided by other Grunt plugins.

To assemble a release build of your project, run the command:
`grunt release`

For a debug build, run the command:
`grunt debug`

> These alias are just a suggestion. You may configure your Grunt tasks in any way you want.

### Integrating with other Grunt tasks

If you wish to minify/optimize your build files, you can add the respective tasks to the `release` task list, __after__ the `angular-build-tool` task.

If you wish to compile files from other languages to javascript (coffeescript, typescript, etc), they must be compiled prior to the build step, so you should add those tasks to the `release` task list __before__ the `angular-build-tool` task.

If you use CSS preprocessors, you may have to add the respective tasks to both the `release` and the `debug` task lists.

### Advanced Use

Read the [Configuration examples](https://github.com/claudio-silva/grunt-angular-build-tool/wiki/Configuration-examples) page for additional information and examples.

### Debugging build failures

 The build tool will display extended information when warnings or errors occur during the build process if you run the `grunt` command with the `-v` option.

You may also force Grunt to ignore some warnings and continue building by running `grunt` with the `--force` option (not recommended, though).

## Contributing

In lieu of a formal styleguide, take care to maintain the existing coding style.

A linter is already present on the project, so just type `grunt` to run it.

If it's apropriate, create some test cases on the `/test` folder and include them as individual tasks on the project's  Gruntfile.

Always start developing by creating a topic branch on your forked repository from the latest tagged stable version on the `master` branch.

When your work is ready, submit a pull request.

__Important:__ all contributions that are accepted will be made available under the project's license.

## Release History

See the [CHANGELOG](https://github.com/claudio-silva/grunt-angular-build-tool/blob/master/CHANGELOG).

## Author

#### Cláudio Silva
- [GitHub profile](http://github.com/claudio-silva)
- [LinkedIn profile](http://www.linkedin.com/pub/cl%C3%A1udio-silva/7/713/367)
