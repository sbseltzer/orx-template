# Orx Template Project

This project is a template that I'm developing as I follow the orx tutorial series. Perhaps you'll like it and adapt it to your own needs. If you think there's a way to improve this template don't hesitate to add an issue for it or submit a pull request! My goal is to make this flexible and easy to adapt.

# Usage

Each directory contains, at the very least, a `README.md` file to explain its purpose and any important details to be aware of.

Clone or download this project and use it as a template for your game. There are some project configuration options in `build/project.lua`. This project provides `src/game.c` and `include/game.h` as starting points for editing code. You can always discard these and use your own if you like. Continue reading for more details on the implications of changing these.

## File Names/Locations

The `src/game.c` file uses orx's bootstrap registration to add the base directory of this project as a default search path for config files. I prefer keeping versioned game content (such as config files) outside of the `bin` folder, but you're welcome to do otherwise. 

By default the built executable name is `Game.exe`, hence the `Game.ini` in the base directory of this project. 

You can move the `.ini` file to the `bin` directory and it will still work. At the time of writing this, if a matching `.ini` exists in both the base directory and next to the executable, the one next to the executable will be chosen.

You can also modify the name of your executable/config file to be named something other than `Game`. Simply edit the `build/project.lua` file. It's as easy as editing a variable.

## Notes on .gitignore and .hgignore

I've set this repository up to ignore the contents of the `dox`/`screenshots` folders, premake-generated files in the `build` folder, non-config files in the `bin` folder, everything but the readme in the `lib` folder, and the `include/orx` folder.

## Project Setup

### Running Premake

Start by running the premake file in the build folder.

It uses a premake file that can be reconfigured relatively easily.

### Orx Libraries/Includes

First ensure orx's libraries and includes can be found during compilation.

There are 3 ways to tell this project how to find the orx libraries/includes. You only need to do one of these.

1. Download or clone orx's source code repository and place it as a sibling directory to this one. Ensure that `../orx/code/` is a valid path from this template project folder. Make sure you build the libraries so that the `../orx/code/lib` directory has content.
2. Put things wherever you want and define an environment variable called `ORX` that points to a folder that contains `include/` and `lib/`. This path is relative to the `build` folder. In this case it's feasible to download prebuilts. If you use bash it may look something like `export ORX=c:/custom/path/to/orx/code` or `export ORX=../../my_orx_prebuilts/orx-nightly-2016-12-21/dev-vs2015-64`.
3. Manually copy and paste the relevant orx libraries to this project's `lib` folder, and copy the contents of orx's includes folder to this project's `include/orx` folder. As before, this could be from a prebuilt download if you so desire.

## Compiling

Typically you'd use the project files generated by premake to compile. This all depends on your OS and whether you specify a project type to generate.

### Makefile

Since I mostly use bash and plaintext editors for development, I use the premake file for project configuration. This means that anytime I add a file to `src` or `includes` I need to run premake again. 

The Makefile you see only exists to add commands that streamline that process. You're welcome to use whatever you like. 

It should work on Linux so long as you have a premake-generated gmake setup (which should be the default). If you want to use that Makefile on Windows, you'll need to modify your environment and install some programs. On Windows I use Git Bash for scripting and Visual Studio 2015 for its compiler. This Makefile assumes you are using a Visual Studio 2015 project config and have Git Bash, GNU Make, and MSBuild in your path. It also assumes the project name is `Game`. If you modify the premake file to change that name, you'll also need to modify the Makefile before you can use it.
