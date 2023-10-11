TS-7-module parse strategy

module parse strategy means how to find a module or what place to find a module

classic : this module parse strategy is not popular for a long time, rare to see.

node : only difference from node module parse strategy is applying for .ts file rather than .js file

relative module path

     ```require(“./xxx”)```

     step 1:   look for   xxx.ts

     step2:     look for from under  xxx dir   , looking for the file named with a name configured in  package.json  main  option . For example, it value may be “main.ts”

     step3:       look for from under  xxx dir   , looking for the file named  with “index.ts”

global module path
`require(“xxx”)`

step1: look for node_modules dir from under cur dir (
inside the node_module :
first look for file xxx.js / xxx.json / xxx.node/ xxx.mjs ,
second look for dir xxx(then , look for the 3rd-party package ’s entry file, based on its package.json ’s main string ’s value like index.ts, main.ts ))

step2: continuously go to one upper level dir to look for node_modules dir until finding it , maybe till root dir of the computer or otherwise intelligence tooltips will tip you that module can not be found.

for module parse strategy , you can reference TS official reference doc  
https://www.typescriptlang.org

www.tslang.cn
