TS-6-go modularization in TS code

as your code amount goes up, we need to apply modularization , which allows you to put your code in different modules and u can combine them by using import statements and export statements , for example, which benefits code maintenance very much, for example, CommonJS, ES Module.

code amount goes up ———> divide and put code into different modules ——> expose a module ’s content by using export statement and import a module’s content by using import statement

frontend modularization standards : ES Modules , CommonJS , amd , umd , system , esnext

TS supports modularization : ES Modules , commonjs

1.  how to use modularization in TS code ? that is , how to import and export a module in TS code? that is, how to write import statements and export statements

just use ES Module modularization standards for unity in TS code to write modularization TS code , no matter what env you are developing for, for example, node , BS ,about which you don’t need to worry since TS code would be compiled into JS code and at meantime tsc will cope with that issue to generate correct compiled result matching the env if you configure tsc option “module” properly（for example, commonjs , es6）.

tips : recommend to use regular export statement as it brings intelligence tooltips

note: don’t append file extension name “.ts” to in your module import statement

2. what’s the compiling result of module code of TS looking like ? or using what modularization standard?

if you config tsc.config file to use ES Module like “es6” as modularization standard of your compiled result , the compiled target is the same to your source TS code from which if you stripe away the types constrains

if you config tsc.config file to use ES Module like “commonjs” as modularization standard of your compiled result , the compiled target is different from your source TS code from which even if you strip away the types constrains

note : ES Modules has 2 types of import and export statements , while commonjs only has one kind of export and import statements and besides the export content will be an object consistently which is different from ES Module .

ES Module basic export and even default export statements will both convert to properties of object of “ moudule.exports” , except for the latter is using “default” as a property of object of “module.exports”

ES Module concrete name import , default import, whole import statements will all convert to require import statement , then using properties of object of “const importedObj = require(“module path”)” to access , except for that for default import, use the property “default” of “imported object” to access

note: if you have import a 3rd party module that doesn’t use ES Module to export but instead use commonjs , you can only use either concrete name import or whole import , or otherwise if you use default import , there will be throwing errors if you haven’t config the tsc options (esModuleInterop : ture ) . in brief, by setting this tsc option true, you can mix up using ES Modules and using commonjs in your TS code. For example, you use commonjs to export a module and then use ES Modules to import that module.

note： inside every Module in compiled result of TS code by tsc, there is a flag of variable manifesting what modularization standard is applied in current module ; except for imported 3rd party modules(which we can’t control what modularization they use, maybe comnonjs, maybe ES Modules ) , all the compiled result modules of TS code modules , that is, JS code modules are applying the same modularization standard like ES Module or commonjs .

3.  best practice :

    — just use ES Modules modularization standard for unity in your TS code

           resons:

               1—— TS code support ES Modules
               2——   ES Modules standard  in TS code  could interact with non-ES Modules modularization standards such as  CommonJS , if you configure  tsc option  “esModuleInterop” as true

                3—— TS code will be compiled  , allowing you to specify compiled result using what modularization standard  such as CommonJS or ES Modules.

4.  if otherwise you have to necessarily write TS modularization code using commonjs modularization standard , how do you do ?

    well, if u purely use commonjs in TS code , surely it’s ok , since TS is a super collection of JS , while you lose types examining(TS code does not support types examining if you purely use commonjs ) , which we don’t want.

module.exports= {

           name: “Tom”,
           sayHello(){
                          console.log(‘hello’)
                  }

}

const myModule = require(“./myModule”)

you should use like this :

export statement :

export = {

           name: “Tom”,
           sayHello(){
                          console.log(‘hello’)
                  }

}

import statement :

import myModule = require(“./myModule”)

or like this(if you configure tsc option “esModuleInterop” as true ):

export statement :

export = {

           name: “Tom”,
           sayHello(){
                          console.log(‘hello’)
                  }

}

import statement :

import myModule from “./myModule”

well , we strongly recommend just use ES modules to write TS modularization code since it’s a trend to use ES modules as a unified modularization standard whether dev BS env JS code or server env node.js / js code , as other modularization standards will be bound to be drown in history river.
