TS-8-interface and type compatibility

extension types : type alias, enum type, interface, class

in real life, what is called interface?

for example, interfaces of your computer, a 3rd party lib providing functions (we usually need to reference its interface doc), frontend calling one interface provided by backend.

concept of interface :

interface is designed to constrain class, object and function ; it’s a standard or contract/agreement (about which we can say it’s a type )that you must obey.

forms of contract(standard):

doc : eg. API doc , which is born with a weakness that it’s a sort of weak constraint / weak standard , cos you may still make mistakes when coding since man could make mistakes, right.

code : eg. interface , which is a type of strong constraint that u must conform to or otherwise you can’t write out code (editor will tip you error )or your code won’t pass compilation so that won’t be able to be executed

when writing backend code , ppl usually will involve using interface. For example, java, c# ,etc.

how to use interface:

note : interface is similar to type alias , but the former has some differences from the latter

one : interface can constrain class , but type alias can’t.

two: we cover this point in later course

note : a common point with type alias:

      interface will not appear in compiled result  just like type alias

1.  interface constraining an object

eg:

interface User {
name: string,
age:number
}

type User = {
name: string,
age:number
}

let user:User = {name:’Tom’,age:18}

note: it’s strongly recommended that u use interface to constrain an object since this means is more popular as the majority of 3rd party libs are using interface to constrain objects

2.  interface constraining a method , a fn

note: since we have TS , we no longer need to memorize many things when writing js code because vscode editor intelligence tooltips will tip you what to write or that there is an error.

case1 : method

interface User {
name: string,
age:number,
sayHello():void // constraint a method : it’s a method, no param , no return value // also sayHello: ()=>void
}

type User = {
name: string,
age:number,
sayHello():void // also sayHello: ()=>void

      }

let user:User = {
name:’Tom’,
age:18,
sayHello(){
console.log(‘hello’)
}
}

case2: fn

type Condition = (n:number)=>boolean

type Condition = {
(n: number): boolean
}

interface Condition {

    (n:number):boolean

}

function sum(numbers:number[],callBack:Condition){
let result = 0
numbers.forEach((n)=>{
if(callBack(n)){

             result += n
         }

        })
        return  result

}

const result = sum([1,2,3,4,5],n=>n%2!==0)

console.log(result ) // expected output 9

note: since we have TS, now we have sense of security to write code , not like writing JS code , in many cases we have no sense of security ; for example, u expect others pass into a fn of callback as a param when invoking your encapsulated fn , but you can’t ensure that or u have to tediously write extra code for type check for the param as part of implementation of the fn.

3. interface face constrain a class : we’ll cover this in later classes.

interface inheriting:

inheriting : a class inheriting another class means a class owning another class of all the members

eg:

```
        class Banner extends  React.Component {


    }

//   at meantime,  in semantics/logic,   Banner is a React Component

```

similarly , an interface can own another interface of all the members through inheriting. That is, one interface can inherit another interface.

besides, an interface can also at one time inherit multiple other interfaces

so, we can combine different interfaces through interface inheriting

```

 interface  A {

  T1: number

}


interface B extends A {

   T2: string
}


const    a:B = {

           T1: 1,
           T2:’ksfeoijoe’
  }






 interface  C {

  T3: boolean

}



interface D extends A, C {

   T4: (n:number):boolean
}

const b:D={

     T1: 1
     T3: true
      T4(n:number){

              return  n%2!==0

       }

}



```

in relation to interface inheriting, type alias can also do similar combination of different constraints through “merge type” , but with nuance( interface inheriting doesn’t allow for son interface overwriting parent interface of members ; merge type will merge same member types if you overwrite a member ).

```
   type A = {


  T1: number

   }

type B = {
  T2: string

}

type C  = {
   //  T1 : string  // if u overwrite a member , here same member will merge  into a merge type  :  number & string
   T3: boolean
 }  & A & B       // merge type  using  symbol ‘&’


const c:C = {

  T1:1,
  T2:’jisjfosidjfo’,
  T3: true
}


```

modifier

concept: modifier is designed to add on info , for example, to a type or a property of a class

note: modifier will not enter into compiled result.

eg:

“readonly”

concept: the modified target will only permit reading

// type UserInfo = {
// id: string
// name: string,
// age: number,
// readonly arr: readonly number[]
// }

interface UserInfo {
id: string
name: string,
age: number,
readonly arr: readonly number[]

}

let userinfo: UserInfo = {
id: 'jife',
name: 'Rainey',
age: 13,
arr: [12, 34, 3]
}

// userinfo.arr = [1, 2]
// userinfo.arr.pop()

const arr: readonly number[] = [1, 4, 6]

// arr = [23,45,9]

// arr[0]=100

type compatiblity : constraint to a variable could be loose ----in some cases/scenes , a type could be compatible downward . For example , a person could be assigned to a duck , as long as the person has features/ characteristics / properties and methods required by the duck of Duck type.

how to implement type compatibility :

one way: using non-literal value to assign to a target variable of specific type

another way: using type asserting when assign , forcedly and specifically telling TS the value actually conforms to the type constraint

//alias: type compatibility judging

type compatibility is designed to adhere to use habits of JS code that JS is not strict with its types check(surely it’s dynamic types check, but being dynamic is not the point here, while the point is not strict types check) ,bringing about some advantages , for example , making JS flexible.

either way, type compatibility sticks to some good habits of JS code

, also making us figure out more about TS ’s static types system , which is including :

type inferring / type caculating

type examining / type judgement

type compatibility

type asserting

1. type compatibility judging for basic types : number, string, boolean, array

   requires being strict , since they are completely different from each other.

so, that is to say, type compatibility doesn’t exist for basic types when u assign a value to a target basic variable , must be strict ,no compatibility

2. type compatibility judging for object : means of duck distinguishing type / child structure distinguishing type

for one scene , for functions provided by 3rd party libs / modules / packages , the corresponding developers return an object in a fn, they don’t know or be unnecessary to know what shape of the returned object —— they just don’t need to think about it since actually they can’t.

or

another scene like frontend invoking a backend API , frontend developers can not customize what shape of the response data

you can use type asserting if you definitely know what type of a specific variable / property should be

interface Duck {
sound: “嘎嘎嘎”
swim():void

}

const person = {
name: ‘a person disguised as a duck ’
ride(){},
sound: “嘎嘎嘎” as “嘎嘎嘎” // type asserting
swim(){
`${this.name}  could release sound ${this.sound}`
}
}

const duck:Duck = person

//but , when u assign a literal object to a variable of a target object constrained by a specific type constraint , TS code will apply strict type check , so the following code will throw an error

const duck:Duck = {
name: ‘a person disguised as a duck ’
ride(){},
sound: “嘎嘎嘎” as “嘎嘎嘎” // type asserting
swim(){
`${this.name}  could release sound ${this.sound}`
}
}

//but , u can fix the error by using type asserting

const duck:Duck = {
name: ‘a person disguised as a duck ’
ride(){},
sound: “嘎嘎嘎” as “嘎嘎嘎” // type asserting
swim(){
`${this.name}  could release sound ${this.sound}`
}
} as Duck // telling TS this is actually a Duck

3.  type compatibility judging for fn : everything goes so smooth and nature u can’t even feel it exists.

    for params, you can reduce them when pass function as value to target fn

for return value, if it’s void in target fn type constrain , u can optionally return or not ; if it’s not void, u must return the specified type of return value
