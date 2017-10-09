+++
title = "Environments"
date =  2017-09-08T02:11:23-04:00
weight = 1
+++

JollofJS uses an environmentally extendable/overridable config system.


Set the environment by passing in `NODE_ENV=myEnv node index.js` and as long as a `myEnv.js` file exists in `config/`, it will be used to override the settings in `config/base.js`.

You can have as many environments as you need.
"development" is the default env if no NODE_ENV is passed in.