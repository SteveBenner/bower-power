# Bower Power!
Those guys at Twitter came up with a marvelous little tool called [Bower](http://bower.io/), which truly is pure awesome-sauce for web developers. The only problem is, they accidentally wrote it in Javascript instead of Ruby. Bower Power is my attempt at solving this dilemma elegantly, without introducing complexity. Think UNIX philosophy, separation of concerns, single responsibility principle, etc. Bower Power won't force you to learn a new DSL, conform to any standards, or deal with some API - it sits invisibly between Bower and you.

## Why?
**Bower is nice, but I find it to be lacking a few key features**  

- No capability to organize or specify custom install locations for packages and individual files
- No security measures (cryptographic signing)
- It uses JSON for config files, and I prefer YAML.

**NPM already has a [bunch](https://github.com/scivey/bower-copy) of [tools](https://github.com/yatskevich/grunt-bower-task) that can offer a solution - what's wrong with using those?**  

I'm mainly a Ruby developer, so my ecosystem relies on Ruby tools. Even if were to come from a Node background though, all the Node packages and Grunt tasks for managing Bower I've seen add unnecessary complexity and/or functionality.

**So what about Ruby gems?**  

I'm not one to re-invent the wheel; in this case my vision of 'the wheel' is just more simple and flexible than existing solutions. For instance, the [bower-rails](https://github.com/42dev/bower-rails) gem provides an entire DSL for using Bower, and I think that's overkill. My aim with `bower-power` is to provide a Ruby interface to Bower that feels and works exactly the same as what already exists.


# Features
- For now this is totally theoretical; **I haven't started coding it yet.**

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

### Assumptions
- `Bowerfile` of a certain format exists

---
#### Similar software to check out
- grunt tasks that work with bundler
- [bundler](https://github.com/LTe/bundler-bower)
- [rails](https://github.com/42dev/bower-rails)