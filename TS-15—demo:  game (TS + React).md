TS-15—demo: game (TS + React)

content :

     1.  how to scaffold  project  —— answer——  React +TS+ create-react-app

     2.   how use  TS + React  to write  React comps

history tech stack: JS + React + create-react-app

tech stack: TS + React + create-react-app ( React official scaffold)

webpack : recursively load modules ——> TS’s tsc: compile a TS module to like esnext modularization standard of JS code ——> JS ——>Babel : lower JS version level ——> single JS file ——> webapck-bundled JS file or webpack-bundled JS files (finial compiled result )

tsc can compile React JSX

TS made by Microsoft

React made by Facebook

TS in its initial stage doesn’t support React’s JSX, but afterwards, it does as Microsoft and Facebook begin to cooperate to have settled this issue. So now, tsc can compile React JSX.

React JSX is an JS object in essence

JSX tsc JS

<div / >     ——tsc compilation processing—>   React.createElement(‘div’)

build / scaffold project

1.  webpack
2.  dva , umijs, next.js , create-create-app

note: entry file is also called starting-up file

react comp types / categories :

display comp : purely responsible for display data purely based on the props u passed ,usually NOT using comp life cycle hooks; therefore, it will most often be defined as a function comp （ alias : a stateless comp）, of which one typical feature is———— no state of self (that is, it not providing any data) , but only having props ——— however, as of recent React versions, function comps can no longer be considered 'stateless'

// me: a display comp r bound to return UI

container comp: purely responsible for processing data , having nothing to do with styles , usually using comp life cycle hooks ; therefore, it will most often be defined as a class comp , of which one typical feature is ————owning state of self

note: a class comp must have a render fn

note: strictly speaking, a container comp ( a class comp ) bears no relation to styles and even to any structure (we can use an empty node like so <> </> ), so in formal project , u better extract an extra comp as a display comp (a function comp) to specically take charge of dealing with styles , and inside it transpond or retransmit (just receive and send) data through props

// me: a container comp strictly speaking , doesn’t add on extra UI to the display comps it calls.

note : so , in React, when design/compose display comp / a function comp , just think about props ( type constraint) and when design/ author container comp / a class comp , just consider (props) , state ( type constraint, provide & maintain ）

note: me: narrowly speaking , a comp should return a UI , or otherwise it better should have been designed as a until fn

note : in React , JSX or TSX , it’s a kind of get-straight mindset / mentality , that is , data ———computing or composing or assembling ———> node / node list , that is , to make node /node list out of data ; go straight to generate / compute / operate node (virtual node for sure) , sort of like JS operate DOM

note: btw, in React, JSX.Element is a type for node ; a node is an JS expression

note :

1.  UI : responsible by display comp (display data—props): structure , styles

2.  logic : responsible by class comp (provide & maintain data—state): computing / logic processing /data logic processing / digital logic processing: input data (state) ——-computing——>output data(state)

note: in React, a node can show or a node’s content can be a string (also node) , or node , or node list

how to use TS in React ? or how to use React combined with TS ?

the answer is , ( note that the pre-acquisition is , file extension change from .jsx to .tsx ) add on type constraints in proper positions

1. how to use TS + React to write a display comp
   === how to constrain a display comp

//define type
interface IProps {
num:number,
// onChange?(n:number):void
onChange?:(n:number)=>void
}
//use defined type to constrain props
//that is, just add on React.FC<IProps> when writing definition of cur display comp

export CountComp: React.FC<IProps> = (props)=>{

            return (

                       <div>
                             <button onClick={
                                   ()=>{ props.onChange ||   props.onChange(props.num-1)
                              }}> -<button/>

                                   <span>{props.num}<span/>

                             <button onClick={
                                     ()=>{ props.onChange || props.onChange(props.num+1)
                         }}>+<button/>

                       <div/>

            )

}

note : React.FC<P> only have 1 generic type referring to the temporory unknown type of props

2. how to use Ts + React to write a class comp
   === how to constrain a class comp

note : React.Component<P,S,SS> have 3 generic types referring to the temporary unknown type of props , of state and of xxx (don’t care about this one )

interface IProps{
num:number,
// onChange?(n:number):void
onChange?:(n:number)=>void
} // used to constrain the type of props , while for sure the same time manifesting what props cur comp has

interface IState {
msg:string
description:string
} // used to constrain the type of state , while for sure the same time manifesting what state cur comp has

//export class CountComp extends React.Component<IProps> {

// or better in this way below

// because otherwise when u call this.setState() , the practical param (position) lose static type check ( state default generic type is {} , which allows property state to be assigned with any object, which means losing type check ),

because method setState belongs to class React.Component<P,S,SS> but u don’t pass concrete type

to the corresponding generic type S

at the 2nd generic type formal pram position of the class React.Component

when u use class React.Component<P,S,SS> // that ’s also explaining why, in a React comp, we need to initialize state —— that is, in React, why to set up default value for state since we do NOT want to lose the type check for state

// type class React.Component<P,S,C> has 3 generic types , P for constraining props of cur comp, S for constraining state of cur camp, C for constraining context of cur comp ; as to generic type C above, we usually don’t need to pass a type , since it has default type {} , and besides we don’t usually use context in dev. btw, if u want to pass type for S(u want to constrain state in your own way / u want to specify type for S representing constraint on state ) , but u don’t mean to constrain props ( u don’t intend to constrain props) , u can pass {} an empty object for P , since its default value is a { } as well.

export class CountComp extends React.Component<IProps,IState> {

        //initilize state
        state:IState = {
            msg:'',
            description:'',
            // test:''
        }

      render(): React.ReactNode {
        // this.state

       // this.setState({
                mag: 123
          })
        return (<div>

            <button onClick={()=>{
                this.props.onChange &&  this.props.onChange(this.props.num-1)
            }}>-</button>

             <span>{this.props.num}</span>

             <button onClick={()=>{
                  this.props.onChange &&  this.props.onChange(this.props.num+1)

             }}>+</button>

      </div>)
      }

}

eg:

when to use a generic type Array ( a type Array depending on a generic type)— Array<T> , its generic type T should be told / specified / passed if needed , so use like this :

const a : Array<number> = [1,2,3]

similarly , when to use a generic type class ( a type class depending on at least one generic type)——— React.Component<P,S,SS> , its generic types should be told/specified / passed if needed , so use like this :

interface IState {
num:number
} // used to constrain the type of state

export class App extends React.Component<{},IState> {

state:IState = {

          num: 0

     }

     render(){

             return  (

                          <CountComp  num={this.state.num}  onChange={n=>{

                                         console.log(n)
                                       this.setState({
                                                  num:n
                                           })
                                }}/>
                  )
     }

}

note: in React , it’s officially recommended not to assign value to certain state/data directly (not to change / modify state/data directly) ; u better use fn setState to change/modify specific states ; it’s because React team thinks the object state is supposed to remain unchanged
