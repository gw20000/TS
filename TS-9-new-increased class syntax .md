TS-9-new-increased class syntax

introduction :

this subject is not relating to OOP , but the new-added-on class syntax has connection with OOP , however, so far , in this part , we don’t talk about OOP programming idea.

properties list :

in TS code , u r not allowed to add new properties to an object dynamically ; an object should be born with certain properties

properties list is designed to state all the existing properties of a class

initializing properties :

there are 2 places / positions where u can initialize properties of a class

    one :     inside  constructor   ( through  param and  assignment statement  , at mean time, u can optionally give property default value )

two: inside properties list ( through property default value , but preacquisition is , you have to know the exact value to assign , therefore , it’s a way only for enum type of properties )

note: if you configure in tsconfig.json "strictPropertyInitialization": true , then properties initialization is a must if u have not modified the properties as optional properties

class User {

          name:string
         age: number
       gender :  ’男’ ｜ ‘女’   =  ‘男’
        pid?: string   //  for an  optional property ,  initialization is not a must
      constructor(name:string, age:number){
            this.name = name
           this.age = age
        }

}

or

class User {

          name:string
         age: number
       gender :  ’男’ ｜ ‘女’
        pid?: string   //  for an optional property ,  initialization is not a must
     //    pid :  string  |  undefined
     //    pid :  string  |  null  = null
      constructor(name:string, age:number, gender: ‘男’ ｜ ‘女’ = ‘男’){
            this.name = name
           this.age = age
           this.gender = gender
        }

}

property can be modified as readonly by using ‘readonly’ right before a property

property can be modified as optional by using “?” right after a property

access modifier : to control access of a specific member of a class

public : either inside or outside the class , in your TS code can access the property

private : to modify a property to restrict its using or access scope to be within the class

protected : we’ll cover it in later class

class User{

private allowNum: number = 3

private curNum: number = 0

constructor(){

     }

pubish(title:string){
if (this.curNum <= this.allowNum)
console.log(‘u have posted an article’+article title : +this.title )
this.curNum++
} else {

            console.log(‘today the number of your posted article  is up to the top limit ’)
      }

}

properties concise writing : in essence a syntax sugar :

in constructor param position ,

[access modifier] [property name ] :[type] = value

eg:

class User {

      constructor(public  name : string  , public  age:number){

        }

}

===

class User {

          name:string
         age: number
      constructor(name:string, age:number){
            this.name = name
           this.age = age
        }

}

or

class User {

         public  name:string
        public  age: number
      constructor(name:string, age:number){
            this.name = name
           this.age = age
        }

}
