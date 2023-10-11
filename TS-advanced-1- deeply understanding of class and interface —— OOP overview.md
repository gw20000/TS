TS-advanced-1- deeply understanding of class and interface —— OOP overview

OOP is a programming mindset

OOP conceptions:

background: why we need / use OOP : why

in OOP program / application , everything is gonna be very detailedly divided into a bunch of classes, based on categories of objects , and everything is seen as an object that entertains its own properties and methods

in this circumstances (adopting OOP to develop a complicated program ) , there will be going to a case that a vast number of APIs (functions , classes, and params ; these r things u need to access) need to be written

and yet because of JS ’s lack of type system, then tremendous APIs will make complication of writing calling APIs dramatically go up——— as a result, there will be a fatal flaw that it extremely easily leads to/ is reduced to / is subject to / suffers / comes across / undergoes errors. ——— and this kind of complication will only have be avoided through type system , not the other way around, for example, human memory , doc , notes , which have no power of compulsory type constraints. That’s why JS is not suitable for developing specially complicated programs/applications———— JS ’s sin : weak type lang , explanative lang , so JS is doomed not suitable for developing specially complicated programs------ u have no idea about the tremendous APIs (eg: is there an API named this ? does this object has this property? how many fn params of this fn , what type of certain fn params , do i have to pass the fn params, what type of one variable, what type of the fn return value )——— Aa a result, in every step u write JS code is under potential risk.

TS brings integral type system , so that no matter how many APIs r to be in a specially complicated program/ project , it will consistently provides complete type check. And this kind of type check is compulsory. So, we can use TS to dev specially complicated program/project since when u write error code , it will give u tips.

in summary, TS brings about a chance that we can adopt OOP to write specially complicated big size frontend application

even though , in theory , OOP , POP, and function programming each of them can deal with complicated problems , over decades, OOP has accumulated abundant precious experience on developing large scale programs or complicated scope programs, yielding/generating a lot of best-optimized fixed or mature patterns targeting many specific complicated scenes , such as authentication management , workflow , etc. —————anyway , we better choose to use OOP to deal with complicated problems targeting complicated scenes , of which JS did not have that ability or chance before.

in summary, OOP has many mature patterns , being capable of dealing with many complicated problems.

frontend trend maybe is going in this direction , that is , combination of frontend and OOP

for examle, frontend next.js like amounts to backend java spring , which is a complete solution adopting OOP

ORM frames , typeorm , mongoose , similar to C# EF

definition: what OOP is : what

OOP : Object Oriented Programming : thinking about problems based on things (classes)

Object: things

Oriented : directed by / based on

OOP : thinking cut-in point is how to divide classes when thinking about how to develop the whole program / the whole question

OOP is a thinking way of programing , but it’s actually very natural : when come to develop a program, i first think about classes (taking classes as thinking cut-in point)—— what some kinds of things r out there to be divided , without thinking about how to complete developing the program whole functionality at all , but, by contrast, just , for example, first focusing on how to complete developing a my-tank class or a component , and then one by one coming to dev other classes or components , and finally u automatically get a project finished. So , by contrast, POP is a scattered way of thinking when to develop a program.

OOP is a kind of programming mindset , bringing the idea that thinking starting point or thinking cut-in point is how to divide objects/classes when thinking about how to develop the whole program

——— it’s one way of thinking that the thinking entrance point or the thinking start point or the thinking cut-in point is how to divide objects/classes when starting thinking about any thing or any problem in developing a program / application/ project

——————simple , about how to develop a program , what’s ur thinking cut-in point throughout developing it? ——— for OOP , the answer is how to divide objects/classes.

POP: Procedure Oriented Programming : thinking about problems based on procedures (modules)

eg: how to dev game tank war ( thinking in POP)
POP ：thinking way: build div —> register event for move ur tank—> write a module for building enemies , register event for fire bullet , which is one way of thinking based on function steps or flows or procedures (me: that is,how to divide modules) as thinking cut-in point when thinking about how to develop the whole program ————— this way of thinking is bearing no problem when solving a small scale project/problem ——— but when to solve a large scale project or a complicated project , the problems come. Because in a big-size or complicated project/program/application , its procedures will often change . As a result, the previous procedure is not suitable for another project——that is, can no longer be reused. Therefore, POP , this kind of programming mindset is NOT suitable for developing a large-scale or complicated project/program/application.

function programming : one way of thinking based on mathematics calculations (caculations or computations) when thinking about how to develop the whole program

how to use : how to use OOP : how

thinking cut-in point is how to divide classes when thinking about how to develop the whole program

so, simple , i first think about what classes r there in a project when coming to develop it.

object : an object is a thing that authentically exists

class : a class is a template that can produce objects , or classes r categories that classify objects

eg:

i am a ppl , and u r all a bunch of ppl ——— that is, we r all individual objects , which authentically exist

then class is the word ppl —— a (abstract) concept , not authentically existing

given that i am God, now there does really exist ppl in the world , ppl is just a concept
ppl (class) : characteristics ——nose , eyes , limbs , gender ; actions———speak ,move, make tools ———————before authentic / concrete ppl(object) come into being , u confirm the concept ppl , that is , class ppl

create a ppl :
new ppl() // an (concrete )object

create another ppl:  
new ppl() // another (concrete )object

these 2 objects r basically different objects ,not the same one , but they r objects of the same class

objects/things of a certain class have some specific characteristics and actions in common , however ,whose values can be different.

eg:

similar , for game tank war

when come to dev a program, thinking in OOP, u first think about how to divide classes :

bullet class : what characteristics , what actions

tank class : my tank , enemy tank

obstacle class: different categories to be made as different classes , characteristics : could it be penetrated , its coordinates

instead, unlike POP, u don’t first think about questions (procedures)like first to do what , and what to do next in detail (but u will think about that later in detail )

so, this (OOP in game tank war) is like going component developing in React , Vue ——— the minimal functionality unit is a component , which is a class , especially in React. when thinking about how to develop the whole program , u first thinking about how to divide classes , and then u start thinking about procedures in detail within a certain class

OOP is a thinking way of programing , but it’s actually very natural : when come to develop a program, i first think about classes (taking classes as thinking cut-in point)—— what some kinds of things r out there to be divided , without thinking about how to complete developing the program whole functionality at all , but by contrast, just , for example, first focusing on how to complete developing a my-tank class or a component , and then one by one coming to dev other classes or components , and finally u automatically get a project finished.

BTW ,

learn roadmap :

1.  OOP in TS (syntax)

2.  game demos (practice)

study approach:

understand ———>generate some ur own thoughts ———> practice ———> …..
