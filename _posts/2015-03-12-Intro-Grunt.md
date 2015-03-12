---
layout: post
title: Making Use of Grunt
permalink: Making Use of Grunt
---

Today's post will involve using Grunt! It is an awesome tool that should be not be feared.

I know, trying new tools can be scary, and especially even more so when so many articles online seems to assume that you already know the basics using this tool. 

But there are a lot of other articles that do start from square one - such as this [one](http://24ways.org/2013/grunt-is-not-weird-and-hard/). 

First, let's cover what Grunt is, and what it does for us, and why it should be used more often in a daily routine of web development. 

[Grunt](http://gruntjs.com/) is a task runner. What does that mean? To paraphrase, they are small applications that automate time-consuming tasks that one does when setting up a project. This alone should give you pause and consider at least trying out Grunt at least a couple of times. 

You can use it for 

- Minification of JS/CSS files
- Compressing jpgs/pngs files
- Concatenating files
- Linting
- Compilation 
- [And so much more!](http://gruntjs.com/plugins)

They have an huge ecosystem of plug-ins and anything you think of, it's bound to be there. 

All righty! Let's fire up that much beloved and trusty console! 

Let's start with installing Grunt. 

Make sure you have NPM and Node.js first. Once those are installed, you install Grunt CLI globally with this command: `npm install -g grunt-cli`


According to [Grunt's site](http://gruntjs.com/getting-started), installing it globally does not mean it installs the Grunt task runner. "The job of the Grunt CLI is simple: run the version of Grunt which has been installed next to a Gruntfile. This allows multiple versions of Grunt to be installed on the same machine simultaneously." 

We are just going to focus on one task for now to simplify the whole process. 

Let's minify files with `grunt-contrib-uglify` plugin. 

Now, navigate to a folder (one that has a bunch of js/css files) which you're willing to experiment Grunt on. Once in that folder, you have two choices in creating a needed file called `package.json`. You can run `npm init`, and just press enter to all the questions and accept the defaults, or you can `touch package.json`, and create the empty file. 

Let's do `npm init`. Ok, so now you have a `package.json` file with all the defaults. Don't worry, you can change the details. =) 

Now, we want to install the `grunt-contrib-uglify` plugin and save its details to the `package.json` file.

So we say: `npm install grunt-contrib-uglify --save-dev`

See the `--save-dev` part? That will make sure the the plugin details will get saved to `package.json` file. 

The next file you need is `Gruntfile.js`. Remember, all you need is `package.json` and `Gruntfile.js` files. So, don't start getting overwhelmed! It's ok. Just keep going forward, and you'll get somewhere. Even getting to the middle of the road is better than staying at the start line forever. And one day, you'll get the end of the road, and Grunt will seem simple. =) 

Here's a sample [http://gruntjs.com/sample-gruntfile](http://gruntjs.com/sample-gruntfile) and its explainer. 

Copy that file. We'll personalize it for our minification. 

All right, open the `Gruntfile.js` file, and let's start personalizing it. 

I've put a copy of what our Gruntfile.js should look like. 

{% highlight javascript %}
module.exports = function(grunt) {

grunt.initConfig({
  uglify: {
    my_target: {
      files: {
        'dest/bootstrap.min.js': ['js/bootstrap.js']
      }
    }
  }
});
  
grunt.loadNpmTasks('grunt-contrib-uglify');

grunt.registerTask('default', ['uglify']);

};

{% endhighlight %}

Look at this line: `'dest/bootstrap.min.js': ['js/bootstrap.js']`. 

Make sure that you have an actual file in the second part that you want to minify. The first part is the minified file generated in the folder `dest`. 

Now we run the magic command: `Grunt`.

Look at the console. It should come up with something like this: 

{% highlight javascript %}
Running "uglify:my_target" (uglify) task
>> 1 file created.
{% endhighlight %}

There you go! Your javascript file, or whichever file you want is now minified! 


