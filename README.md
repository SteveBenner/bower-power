# Bower Power!
Those guys at Twitter came up with a marvelous little tool called [Bower](http://bower.io/), which truly is pure awesome-sauce for web developers. The only problem is, they accidentally wrote it in Javascript instead of Ruby. Bower Power is my attempt at solving this dilemma elegantly, without introducing complexity. Think UNIX philosophy, separation of concerns, single responsibility principle, etc. Bower Power won't force you to learn a new DSL, conform to any standards, or deal with some API - it sits invisibly between Bower and you.

## Why?
**What's wrong with Bower?**  

- No capability to organize or specify custom install locations for packages and individual files
- It uses JSON for config files, and I prefer YAML.
- No security measures (cryptographic signing)

**NPM already has a [bunch](https://github.com/scivey/bower-copy) of [tools](https://github.com/yatskevich/grunt-bower-task) that might solve this issue - what's wrong with using those?**  

I'm mainly a Ruby developer, so my ecosystem relies on Ruby tools. Even if were to come from a Node background though, most of the Node packages and Grunt tasks used for managing Bower add unnecessary complexity and/or functionality.

**So what about Ruby gems?**  

I'm not one to re-invent the wheel; in this case my vision of 'the wheel' is just more simple and flexible than existing solutions. The [bower-rails](https://github.com/42dev/bower-rails) gem provides an entire DSL for using Bower, but `bower-power` is meant to be an invisible wrapper around Bower.


# Features
- Allows you to install bower assets into arbitrary destinations, based on simple configuration
- Provides four means of configuration


## Asset Management

### Ideas
- mode allowing you to store configuration data within the actual `.bowerrc` file itself; this works as follows:
    1. parse in the `.bowerrc`, storing config data and then removing it from the JSON file
    2. run `bower install` as normal
    3. move files and perform other functions
    4. write data back to `.bowerrc` JSON file
- use key-value pair `configuration: <name of gem>` to identify the config data file as belonging to the gem (use in `.bowerrc` as well)
- actually allow for four options for configuration
    1. YAML config file
    2. use `bower.json`
    3. use `.bowerrc`
    4. CLI parameters

## Assumptions
- `Bowerfile` will be properly identified
- 
    
## TODO:
- bower install 
- bower uninstall

#### Similar software to check out
- grunt tasks that work with bundler
- [bundler](https://github.com/LTe/bundler-bower)
- [rails](https://github.com/42dev/bower-rails)