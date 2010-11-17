# soloist_intro

!SLIDE

# Soloist Intro - Was: Workstation Chef

## mkocher@pivotallabs.com

## It's not dead, it's merely decomposing.

!SLIDE

# What is Soloist

Soloist answers the question "how do I get started using chef with my project?"

It's a simple way to run chef solo, which just enough to get you started quickly.

It reads a yaml soloistrc file, generates the json file and rb file necessary to run chef-solo, and runs it.

!SLIDE
# What isn't Soloist

* A fork of chef
* Not chef

!SLIDE
# How do I get started? (on a mac)

* Install X Code (hint: afp://pivotal@union/ => general temporary storage => installers => xcode )

``` bash
sudo gem install soloist
```
Then get your recipes

## bootstrapping:
``` bash
sh -c 'mkdir pivotal_workstation && cd pivotal_workstation && \
curl -L http://github.com/mkocher/pivotal_workstation/tarball/master | \
gunzip | tar xvf - --strip=1'
```
## Not bootstrapping?
git submodule (or check the recipes into the project)

Then create a soloistrc...

!SLIDE
# Soloistrc

The soloistrc is a simplified way to tell chef what you want to do.  When you run _soloist_, it recurses up the tree looking for a soloistrc file, and uses the first one it encounters.  This means you can be anywhere in your project, and "soloist" is the only command you need to type.

Example, in the directory containing pivotal_wrkstation:
``` yaml
Cookbook_Paths:
- .
Recipes:
- pivotal_workstation::text_mate
- pivotal_workstation::git
- pivotal_workstation::git_config_global_defaults
- pivotal_workstation::bash_profile-better_history
- pivotal_workstation::bash_path_order
- pivotal_workstation::bash_profile
- pivotal_workstation::git_config_global_defaults
- pivotal_workstation::inputrc
- pivotal_workstation::osx_turn_on_locate
- pivotal_workstation::textmate_set_defaults
- pivotal_workstation::rvm
- pivotal_workstation::mysql

```

!SLIDE
# Workstation Chef
## An Update


!SLIDE
# Style

The pivotal_workstation cookbook is a (mostly) decomposable set of recipes.  Your project can compose through meta recipes which describe roles, and mix and match your own cookbooks and recipes.

Overriding pivotal_workstation is possible, though probably not necessary unless you want to reuse a recipe that depends on a recipe you need to modify.

Overriding attributes is easy to do, you'll just need to create your own cookbook, and provide the overrides.

!SLIDE
# Go forth

Automate configuration. Repeatable. Documented. We write tests to make sure our code does the same thing tomorrow that it does today. ???

# Turtles all the way down.