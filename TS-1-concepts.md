TS-1-concepts

TypeScript is JavaScript with syntax for types.

simply, TS === JS + type system (static type examining)=== JS + syntax for types（types constrains）

background : JS’s sin : JS is a weak type language and is a explanation language , designed for implementing simple functions in BS or for not big size project , which leads to frontend engineers are subject to spending a large amount of time killing not critical bugs caused by weak type variables and have to find the bugs until the JS code runs, since JS is a explanation type language which means it doesn’t need to be compiled but instead be executed directly.

     JS’s sins are  including:   ( in summary,  weak type lang ,  explanative lang )

     1)   take a  type-changeable  variable as fixed type of variable  as you are allowed to change  a variable’s type in JS code

      2)  you have to  wait until runtime to find JS code errors, since it’s a explanation type language

      3)  JS code  doesn’t check whether a variable name , function name , or a member  is existing or not , when authoring JS code.

    overall,   these JS’s sins could trigger tremendous  errors  but not related to functions , especially in an intermediate or large size project , so that leading to lots of time spent in eliminating these little bugs.

    in brief,  JS code’s sin  is mainly  types errors

    in brief,  JS code’s sin is ,   JS doesn’t have strict  check , for example, leading to  that   even though u have written error code,  u r not aware of that.

in brief, JS code’s sin is , JS is explanation lang , whose errors r only be able to be found during runtime——JS only has dynamic type check.

back in 2012, Microsoft found using JS to develop frontend projects is painful because you will be subject to large amounts of time spent on debugging related to types in JS

so the company aimed to develop a new language that could be compatible with JS and meanwhile solve the annoying issues regarding to types in JS.

      2009: node :     npm  , CommonJS
      2012:  TS  :         open source ,  embrace ES norms
      2015:   ES2015 : ES module, promise,fetch , Class

TS functions : is to kill / avoid JS’s sin that JS is a weak type language and JS(which means the type of a variable allow for being changed) is explanation type language(which means error have to be found until JS code runs, and btw JS is used to be run directly since it’s a explanation type language). That is, TS is able to find and tip most errors in dev time when authoring code in editors such as VS-Code, finally blazing beneficial for saving dev time so as to shorten the project dev cycle, which is quite important to a company because saving time is saving costs.

    1)   in editing time  and  compiling time , to tip errors that won’t be tipped in JS code  brings  great benefits including  getting earlier to find errors in TS code  , meanwhile reducing errors committed by the developer when writing TS code ,and consequently not having to wait until runtime to find the errors in comparison to writing JS code.

    2)  subsequently, leading to dramatically shrinking debug time, so as to reduce dev cycle of a project involving use of JS

    3) otherwise with a surprise,  boosting support for  JS OOP , which is a mindset that refers to the thinking of  entry point when analyzing a function is how to arrange objects, so that now using TS we can write better OOP code  than using JS.

vs-code tooltips for TS : intelligence tooltips( static type examining, including types inferring) /types tips

trigger vs code intelligence tooltips : you still author pure JS code without using any piece of extra syntax(TS syntax) , and u just need to change js files’ extension name .js to .ts

             code editing time (intelligence tooltips by vs-code)

           applying to variables, functions, functions params,  functions return values

TS definition: JS superset ; optional type system (static type examining, including types inferring ).

optional : you still author pure JS code , since you could choose not to use TS type system by not adding extra syntax to JS code.

       in other words,  you can choose to use  TS static type system  , or you can choose not to by not adding on types constraints , but for sure, types inferring still works for /has an effect on your code.

static : type examining happens before runtime, that is, compiling time ( type examining happens when run tsc to convert xxx.ts to xxx.js , that is , during compiling time )

type system: examine the types of variables, functions, functions params, functions return values while converting TS code to JS code, cutting loose or striping away the syntax for types.

       So, note that  TS is not taking part in type examining during runtime, since during runtime, the code           executed is JS rather than TS .

when coding TS code, you can optionally add on types constraints /types definition/ types description to variables, functions params, functions return values , better noting wether type inferring works out the correct type , if yes (at most spots, yes), you don’t need to add on type constraint to the variable , function param ,or function return value, making TS code more concise.

    —— how to  add types constraints (info) when writing TS code ?
    —— append   “ : type “  to a variable , a function param , or a function return value

bable: es6—>es5

tsc : TS compiler: TS —> JS

—— in detail, how to constrain a variable ,a function param ,or a function return value as a specified type?

——- number, string, boolean, number[] or Array<number> ( in which Array is the constructor fn of array), object (which is not often used because it’s not precisely describing/constraining/defining the type)

to conclude:

TS is not adding to any functions than JS; it’s just granting more constrains to JS only in syntax aspect.

in TS, we can manage to use static types examining effortlessly

types constraints affect your code during compiling time only

types constraints only work in compiling time, being given to tsc to parse

because vscode supports intelligence tooltips for TS code , and meanwhile because TS code has static types system , so in edit time of coding TS code in vscode , intelligence tooltips is very helpful finding out errors and giving intelligence tooltips for you.

either way, TS brings us very considerable benefits including intelligence tooltips involving vscode and TS code’s static types system which means these two entities could work together, static types examining. even when u choose not to use TS code static types examining , intelligence tooltips still work.

TS brings considerable convenience to reduce the chance/risk/oppotunities of you making mistakes when coding TS code.

TS is designed to define types , that is, types constraints to avoid errors subsequently happen in runtime ; after defining the types, about how to write TS code , it just the same as writing JS code, except for adding on types constrains or already existing types constraints .

you gain more integral intelligence tooltips when you choose to use TS code’s static types system in more places in your TS code, making your code get more integral types examining, making it more impossible for u to make mistakes.

TS is designed to reduce our burden rather than add to our trouble.

TS bring us convenience ( especially when u choose to use TS static types system) while coding TS code through its static types system collaborating with vscode intelligence tooltips support for TS code

what u need to do : add on types constraints to you TS code (combine defining types & then referencing the types and straight adding on types constraints )
what you gain : integral intelligence tooltips , reduction to chances for u to make mistakes

every place in your code gets type tooltips （integral intelligence tooltips） on basis of types examining , making it hard for you to make mistakes

for one difference from JS code , besides types examining , in TS code there can’t exist any stuff that doesn’t exist when u r editing code as intelligence tooltips will tip u or tsc will throw error in compiling time.

TS only work before runtime

TS is designed to avoid us writing error code

if u don’t use TS optional static type sys sufficiently, in many positions there r no intelligence tooltip, wrongly written fn names , which will lead many potential issues

on one hand , TS’s optional static type sys makes your have less chance to write error code , on the other hand , it makes it much easier / more effortless to write code.

to learn TS is actually to learn 2 things ( or one thing that is TS’s optional static type system):

1.  how to make / define / design types

2.  how to constraint entities (string, number,boolean, array, class, object, fn, fn param , fn return value ) by using types

note: if you don’t use TS’s optional static type system , that means u can’t use/get/gain/acquire TS’s type check / TS’s type constraints (even though that, intelligence tooltips still kinda works for you), as a result , u end up writing JS code rather than TS code.

simple, if u don’t constrain entities , u r writing JS code.

TS types:

basic types : string , number, boolean

extension types: array, object, class , fn , union type, type alias, enum, interface , overlap type, type compatibility( non-literal , type asserting )

supplements to type constraint :

generic type

generic type constraint

multiple generic types

they can be seen as types as well.

in conclusion, if u use TS , better choose to apply strict type constraint to every position , consequently to dramatically avoid writing low level error code later on ,

so that lead to reducing debug time,

as a result , cut back on the cost of developing a project.

besides, since TS’s static type system is optional , i highly recommend we can choose to progressively add type constraints to your TS code , if u r not fully mastering the usage of TS’s optional static type system , rather than feel like you are forced or pushed to add type constraint to every position , which maybe takes you lots of time.

TS is designed to reduce / cut down / decrease / cut back on / bring down / lower our trouble in stead of adding to / increase / bring up our trouble. So don’t feel pressure using TS , as its static type system is optional , and u can use / add on type constraints progressively

TS provides benefits:

1.  have intelligence tooltips in time for types of an entity and existence of an entity when writing code

2.  have intelligence tooltips in time for type errors of an entity and existence-related errors of an entity when writing code

note: even though, in a .ts file or .tsx file , u write pure JS code, u will still gain a big advantage that intelligence tooltips still works for native/built-in entities , for example, built-in APIs, built-in comps , except for working for your custom entities , such as, your custom fns (APIs) , your custom comps , etc.

so that , using TS to write code offers u a sense of security (
ever no intelligence tooltips for these:
is this property existing ?  
should i pass the param to certain fn ?  
 whether does certain fn have return value?  
 what props should pass to the comp , as i don’t know the names of the props?  
 what the types of props should i pass to the comp?  
 does certain fn or comp to which i can pass a callback fn ?
things like that. Those now r all the way settled by using TS static type system / by adding on type constraints to the entities )

in brief, in other words, using TS to write code offers u intelligence tooltips to tip u errors or potential errors before runtime ( that is, while editing code and while compiling time).

eg: for usage

define type constraint , for example, for an object , including :

      1.  2 required  properties ,  2 optional  methods

      2.    respect types of the properties ,   respect types of the methods , consisting of  :  how many  the fn params  ,   the params’ types ,    and  the type of the fn return value.

for the constraint above , we can implement by using interface.

then use the defined type constraint above to constrain an entity when defining or declaring the entity

by adding on the constraint above to the entity , that is, an object

fully use TS ——> every step while u r writing code / every position in ur code gains strict type check ——> u r unlikely to write error code.

in TS code, to declare a variable and meanwhile to initialize the variable with a literal value , which will be successful for type inferring offered by vscode combined with TS optional static type sys

TS’s benefits : 1. intelligence tooltips 2. type check / type constraints

or

TS’s benefits : having sense of security while writing code

in essence : TS type sys : through code to constrain the types/shapes of entities which include : entities of basic types and entities of extended types , in relation to types(dynamic entity types) in JS

basic types: string, number, boolean , null, undefined , fn , array, object , class

extended types: literality , union, type alias, overlap, enum( string ~ , number~), interface

a feature of types : type compatibility ( use non-literality or type asserting (manually forcedly tell TS what the type of an particular entity ) , and non-empty asserting)

a feature of types : modifier ( modifiers can apply to a type and a property as well)

a supplement to types : generic type

a supplement to generic type : generic type constraint

a natural thing : multiple generic types

with this in mind :

1.  given that u define a type or gain a provided type

2.  then use the type ( such as , a literal type , union type , type alias , enum type , interface , class) to constrain a entity ——— it means to constrain the type of the entity as the type u defined or gained

in conclusion:

conception:

indispensable : why we need type system ?

remember : code constraints r much stronger than contraint ability of docs (eg. API docs (such as , network APIs , fn APIs , comp APIs of frameworks, comp APIs of UI libs ). That’s why we need type sys.

remember : JS is originally designed for little functionality on Web Page , rather than for medium or big size project.

but it’s such a matter of urgency that JS should be capable of writing medium or big size projects , since frontend app is becoming more and more function-complicated and larger and larger in scale partly because of multiple kinds of ends. That’s why we need type sys.

remember : using type sys can reduce debug time and hence lower / cut back on / decrease /reduce development costs. That’s why we need type sys.

optional : using type system is not compulsory

TS is a super set of JS , with an addition of optional type sys : it’s not compulsory to require u to change the way u write JS code , but actually it’s not always completely optional , since u have to use type sys / type constraint in some cases like when TS combines with React , u have to constrain the type of state of a class comp as IState (u have to pass / specify concrete type for the generic type S of class React.Component<P,S,SS>)

static: type check only happens while u writing TS code and compiling TS code

TS code (source code ) ——> tsc compile TS code ( strip away type constraints)——> JS code

TS ’s type check is happening or effecting at the point of writing code as well as TS compiling time , rathe than at the point of JS runtime

how to constrain types :  
target positions/entities for type check/ type constraint:
scope of target entities constrained by types : basically, we r gonna constrain the types of variables , fn params and fn return values , these 3 positions / entities .

available types for type check / type constraint :
scope of selectable types for constraint: one of what possible types could we use to constrain the type of a particular position/entity as when writing the definition or statement of a variable or fn ?

basic types: stirng, number , boolean, array, object , void, never , undefined, null

custom types / extended types: type alias , enum (string, number) , interface, class , and among those 4 extended types , enum and class is gonna appear in compiled result , and the rest isn’t .

custom types: literal type （ eg. string literal type, number literal type , meta array, object literal type , and more ） , union type, overlap type

literal type in many cases will be used combined with union type , which makes it function-similar to enum , but not perfect than enum for constraining the type of certain position as only being able to get a possible value within a fixed scale

using literal type combined with union type and type alias has its flaw/weakness/ vulnerability in the aspect of code maintenance which enum can perfectly settle by contrast. ——— real value doesn’t matter , what concerns is logic value ——————enum is specially designed for getting a value from a fixed scale

for another thing about literal type, object literal type which can constrain the type of an object in detail / in a detailed way usually is used combined with / in combination with type alias

note: enum—> tsc compile——>object

           TS class——> tsc comile——->  JS class

one more feature of TS class than JS class: property list  
 one common feature between TS class and JS class : modifier ( readonly , access modifiers: public , private , protected )

void: means a fn doesn’t have return value , that is , returns undefined
never : means a fn could throw error or could have a endless loop ———- a fn could never end

undefined , null : they r sub types of all other types, and by default , they can be assign to any other type ( we can adjust this behavior by configuring “strict” or “strictNullCheck” in tsc config file )

TS’s type compatibility : use non-literal-type , use type asserting , use non-empty asserting

TS’s type compatibility :TS says: in many occasions, when i need to judge/distinguish if some type of a stuff meets the type required , i don’t care what a stuff it is , but i just care / concern if this stuff entertains some specific features / characteristics ———— means of duck distinguishing type (eg, to distinguish / judge whether a stuff is a duck , just need to confirm it’s capable of giving out a sound like “GaGaGa”——that’s the only characteristic i need to confirm ) , means of child structure distinguishing type ——— TS adopts this kind of way to do type compatibility judgement , because Microsoft TS team thinks about 2 points : habits of wring JS code and that TS’s type sys is static unlike Java , C# .

type asserting , this point will often be got across in writing / developing Ajax request

generic type : in fact, a type variable or formal type param , a temporarily unknown type , in fact , a type , a supplement to types , and meaning one type depends on one temporally unknown type————— teacher says generic type is designed for undoing / eliminating / striping away the couple between types and functionality

note : couple , in other words, is connection or relation ,so to undo couple is to cut off the connection or relation between 2 or more particular things. ——— this is when to use generic type.

what is generic type? （ a type formal param） when to use generic type? (when u need to cut off couple between types and functionality ) how to use generic type? (simple , add on generic type to type definition )

generic type constraint: in fact , a type , a supplement to generic type

multiple generic type: it’s a natural thing if u have generic type , meaning an type depends on multiple temporarily unknown types

to conclude:

TS will do type inferring and type check based on the constraints u have added on to ur code and the code u have written

TS is designed to type-constrain the type of 3 positions : variable , fn param, fn return value

how to use TS —— just add on type constraints to these 3 positons.
