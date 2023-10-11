TS-4-extension types

TS extension types purpose: are designed to solve many special scenarios and optimize some of previous TS code , which are only engaged in using TS basic type.

TS extension types definition ： besides TS native types, we dev some new types , as TS primitive types are not adequate for our need.

to constrain a variable’s value scale , we may choose to use :

       literality types  +  union

but the problems are :

1.  unable to reuse the type , leading to repeated code ( this issue can be solved by combining using types aliases )

2.  logic meanings and authentic values are coupled , leading to difficult maintenance , that is, when you modify authentic values , you may have to do a huge number of modifications in your code (so to solve this problem, we need to extract logics meanings from authentic meanings , or we could say we need to separate these two meanings)

3.  literality types will not exist in compiling result , leading to being unable to dynamically reading literality types (to settle this, we need to find a type that will still exist in compiling result )

so , enumerability types come into being , to settle the above vulnerabilities

enumerability types like other types certainly take part in compiling process, but besides they will not be cut loose during compiling time and therefore they subsequently appear in compiling result so that we can access them in runtime, that is, dynamically.

a enumerability type will be compiled into an object ,in essence.

so, when to constrain a variable’s value scale , we better use enumerability types , while not suggesting you use “ literality types + union + types aliases“ , which can not escape from the last 2 flaws above.

enumerability types definition :
enum enumerability type name {
logic meaning name 1 = authentic value 1 ,
logic meaning name 2 = authentic value 2,
…..
}

or

enum enumerability type name {
string name 1 = value 1 ,
string name 2 = value 2,
…..
}

eg: string enum

    enum  Gender{

          male= ’男’,
          female=‘女’

}

let gender : Gender

gender = Gender.male

gender = Gender.female

Object.values(Gender).forEach((value)=>{

        console.log(value)

})

eg: number enum

enum Level {

          level1 = 1,
         level2,
        level3

}

let level : Level

level = Level.level1

level = Level.level2

Object.values(Level).forEach((value)=>{

        console.log(value)

})
