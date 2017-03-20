---
title: "Stop Elastic Beanstalk from Running npm install"
date: 2016-10-10 18:11:09
layout: post
author: "k2byew"
---
Just remove `package.json` if don't want AWS Elastic Beanstalk to run `npm install`, or rename it, eg. `package-off.json`

Some packages do require `package.json` to run, so those will break. Can potentially add in someting like this as a workaround:

From:

    mypackage = require "package.json"

To:

    try
      mypackage = require "package.json"
    catch err
      mypackage = require "package-off.json"


Gotcha's:

Nodejs expects a JSON file but the file extension doesn't match, it will throw errors. So keep the `.json` extension when disabling `package.json`

If your build machine has a different architecture to the Elastic Beanstalk machines, some pacakges requiring binary builds won't work since it won't be compiled for the correct target.


References:

[http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create_deploy_nodejs.container.html](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create_deploy_nodejs.container.html)

[http://stackoverflow.com/questions/21200251/avoid-rebuilding-node-modules-in-elastic-beanstalk](http://stackoverflow.com/questions/21200251/avoid-rebuilding-node-modules-in-elastic-beanstalk)
