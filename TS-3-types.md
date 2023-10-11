TS-3-types

TS basis types === JS types + other TS basic types

JS types including:

string, number , boolean, object, array, null, undefined

other TS basic types including:

union , void, never, literality, tuple, any

note: type of any will bypass types examination system can be able to be assigned to any other type of variable.

type alias : a name for a specific existing type (me: it’s a reference representing the existing type, making types reusable , making code more concise and easier to maintain. )

usage eg.:

         type  Gender =  “male” | “female”

         type  User = {

               name: string
              age:number
              gender: Gender
        }

type alias could be very useful mostly

can allow for avoiding writing the same type constraint / definition / description repeatedly maybe in many places in your code , which benefits code conciseness and code maintenance

types constraints in relation to functions :

function reload : right before a function implement , state multiple cases of calling the function (me: to get more exact types constraints info as you desire exactly )

eg:
/\*

        get  the  result of  a plus b

_/
function combine(a:number,b:number):number
/_

        get  the  result of  a multiplied by  b   or of  multiplying a and b

\*/
function combine(a:string, b:string):string
function combine(a:number | sting, b: number | string ) : number | string {

              if( typeof a === ’number’ && typeof b === ‘number ’){
                         return  a * b
                   }
            else if (typeof a===‘string’ && typeof b===‘string’) {
                        return  a + b
                  }

           throw  new Error(‘a and b must have the same type’)
    }

optional params: a function param that you can choose not to pass into when calling the function

eg:

       function sum(a:number, b:number, c?:number){
               if(c){
                       return a + b + c
                  }
                else  return  a +b
       }

            sum(1,2,3)
            sum(1,2)

default params : the same as default param of a function in JS

            a default param is certain to be  an optional param , which means  a default param amounts to not passing the param when calling the function


       function sum(a:number, b:number, c:number = 0){
               if(c){
                       return a + b + c
                  }
                else  return  a +b
       }


      sum (1,2)

note that optional params and default params better are put in the end of the arguments list of a function or otherwise it’s meaningless using them.
