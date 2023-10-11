TS-12-generic type

background: when use type constraints, for example , define a fn with type constraints, sometimes we may lose some type info ,such as type consistence at multiple positions , type connection at multiple positions , leading to that we can’t use TS ’s static type check. how to settle this problem? —how to hold back losing those info? so far, we have to turn to generic type.

sometimes when implement code , it has nothing to do with types, but when we constrain types , we need types info and this is the moment u need generic type

in brief, when using type constraints , we sometimes may lose some type info. This moment we can use generic type to constrain type info. So, generic type is an indispensable supplement to type constraints, if we don’t have an alternative .

TS says words to developer :

when defining a class, fn , interface, or type alias, in some cases, u r unable to know some type in some positions , then use a generic type (a type variable )

TS using generic type says words to code :

i don’t know what type u r , when u use/ write calling me ( a class, fn , interface, or type alias,) , u will naturally tell me the related types (same type ) to the generic type ( that is, the concrete generic type )

in brief:

background :

1 . sometimes defining type constraints , u r doomed to lose some type info ( info like type consistence, type connection, even if u constrain all the related positions as type of “any” ).

2.  sometimes defining type constraints, u r unable to know the concrete type when defining a fn , class, interface, or type

in brief:

when a fn , class , interface, or type alias is related to a temporary unknown type , u can use generic type

a generic type T says: u tell me what type it is , it is what type.

    whatever type  u  tell me ,   the generic type of the entity is that type , and the  entity-inside positions related to that generic type all is that type.

generic type definition: it’s a type that adheres to and belongs to a fn , a class, an interface , or a type alias.

note: generic type is equivalent to / amounts to a type variable (me: a form param) , of which we don’t know the value when defining , for example, defining a fn, so we just use the variable to represent an unknown type when defining , and then until writing calling, You will know , passing concrete generic type to tell TS , or TS will know by inferring the concrete type if TS is able to do that based on your defining and calling info.

in object-oriented programming, generic type can be instantiated with any other type.

it’s a technique in programming , allowing the developer to author more flexible and reusable code , by not specifying a concrete type , but instead specifying a generic type ( that could be seen as a type variable , ( me: a formal / form type param / argument )).

eg:

when defining a fn , u don’t know what type of the array ( this array is a formal param) , so then u can use a generic type (me: a formal type param)

when writing calling the fn , u know the concrete type of the generic type , so pass it to the generic type , or TS can infer the concrete type based on the practical param value ’s type

// when writing definition , we use a generic type

function take<T> (arr:<T>[],n:number):<T>[]{

                   if(n>arr.length){
                     return  arr
               }else{

                     const  newArr : <T> []= []
                   for(let i=0;i<n;i++){
                      newArr.push(arr.shift())
                 }
                   return newArr
               }

}

take<number>([2,3,5,6,27],3) // directly telling TS the concrete generic type of the generic type belonging to the fn take when writing calling the fn take . // we may specify the concrete generic type of the generic type belonging to the fn take when writing calling the fn take

or

take([2,3,5,6,27],3) // TS will infer the concrete generic type based on the practical param u pass which has a concrete type number[]

principle/ mentality roadmap / mindset roadmap : when calling, for example, a fn or a class , TS infer the concrete type of the generic type of the fn or of the class based on the type of your passing practical param , or u pass/specify the concrete type of the generic type of the fn or of the class ——> then everywhere of the related positions in the fn or in the class , including positions in the interfaces and positions in the type aliases, gets an identical concrete type

Through the class's generic type, we can constrain all the properties and methods (all the related positions to the generic type) that are inside the class and that are related to the generic type.

Through the fn’s generic type, we can constrain all the variables and functions (all the related positions to the generic type) that are inside the fn and that are related to the generic type.

functionality : generic type is designed to help ur TS code get more integral and more consistent type check

usage : how to use generic type in code : recipe: take a generic type as a formal type param or simply a type variable , to serve as an unknown type to occupy related type positions

1.  how to use generic type in fn :

defining a fn , right after fn name write as ````` [fn name] <generic type name> ``````

eg:
//to define a generic type fn : when define a fn , using generic type to tell TS some info about this fn ———- the type of each member of the param arr , the type of return value ,and the type of local variable result r all consistent T

function take<T>(arr:T[],n):T[]{

        if(n>arr.length){
           return  arr
       } else {
             const  result:T[] = []
               for(let i=0; i<n; i++){
               result.push(arr.shift())
                }
                return  result
         }

}

take<number>([1,21,32,4,5,8],2) // passing number to T , now telling TS that concrete generic type T’s value is number , which refers to that at multiple positions in the fn , each array member ’s type is number

take([1,21,32,4,5,8],2) // TS will infer concrete generic type based on practical param arr’s value [1,21,32,4,5,8] whose type is number[]

note: the fn take has a generic T and the practice concrete type value of generic type T is confirmed until writing calling the fn

note: concrete generic type value is not known/confirmed until write invoking

note: mostly , TS can infer concrete generic type : In many cases, you may not have to pass or write generic type when calling,
since TS will be able to intelligently infer the concrete type value of generic type,
based on the practical parameters you pass,
but the pre-acquisition is that you have defined generic type in the form parameters.

note: if u don’t pass value/type to generic type , and nor do u define generic type in form params , TS will not be able to infer concrete value/type of generic type ; if TS has not been able to infer value/type of generic type , the default value/type would be an empty object , as we know empty object has the best type compatibility (child structure distinguishing type) —— empty doesn’t have any characteristic , so that any object can be assigned to it .

note: we can set default value for generic type ,however, which is rarely seen . After u set default value for generic type, it works if TS can’t infer the concrete generic type nor do you pass concrete generic type value to generic type when calling

function take<T=number>(arr:T[],n):T[]{

        if(n>arr.length){
           return  arr
       } else {
             const  result:T[] = []
               for(let i=0; i<n; i++){
               result.push(arr.shift())
                }
                return  result
         }

}

1.  how to use generic type in a class, interface, or type alias :

in the same way, add [generic type name] right after a class, interface, or type alias :

// use generic type in interface
interface CallBack<T> {

          (n:number):T[]

}

// use generic type in type alias  
 type CallBack<T> = {
(n:number):T[]
}

or

type CallBack<T> = (n:number)=>T[]

// use generic type in class
class ArrayHelper<T>{

}

const arr2: Array<number> = [1, 2, 45, 3433]

// in fact , this is using generic type in an interface , so when u specify the concrete generic type of a generic type , it , actually , a concrete type , for example, here is an interface : Array is an interface , and number is a concrete generic type u pass or specify to the generic type belonging to the interface Array. so here in essence, u r using an interface to constrain the type of a variable arr2.

interface Array<T>{
forEach(value:T, index:number, array:T[]):void
}
// if not using generic type , no matter how u write defining this interface Array , u will never write it correctly. Because u lose some type related info

in conclusion :

to define a generic type fn / class / interface/ type alias is to define a fn / class / interface/ type alias having / depending on one or more than one unknown type ( but , a generic type can be assigned a default type and can be constrained by one or more than one specified type as well )

when writing using the defined generic type fn / class / interface / type alias , pass / specify the concrete type or types

generic types are a supplement to type constrains
