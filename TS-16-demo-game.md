TS-16-demo-game

1.  how to divide / formulate comps : there r a number of other division ways out there , this one being just one of them

divide this application program—game into 3 comps : ChessComp , ChessBoardComp, GameComp

        relationships between those 3 comps  is  inclusive  ;  each  comp has its own states ( that is ,  provide some data )  ; for or  example ,    ChessComp has 3 states (empty, red, black)  ,and  ChessBoradComp provides  some data ,   and  GameComp provides some data

2.  as to how to choose to define a comp between as a display comp or as a class comp , this point , we covered in last class.

note : constraint of a comp’s props is an object usually , and the same to a comp’s state

3. styles: css , less ( css pre-processor ) , sass (css pre-processor) , css modules ( can avoid style classes’s conflicts/clashes/collisions )

choose to use sass , bringing us benefits as follow: reusable style values , reusable styles , modular scss ( which is capable of avoiding collision between same-named class names in different scss files , and able to use styles (classnames , animation names) in JS dynamically)

note: if u want to write JSX , TSX language code, u must import React

note: JSX’s or TSX lang’s typical characteristic is , one node is taken as an JS or TS expression

JSX === JS + XML === XML merge into JS

TSX === TS + XML === XML merge into TS

in conclusion:
thoughts of dev project : scaffold project with scaffold ——> install and config like downloading css preprocessor sass and config global sass by installing @craco and configuring it. —— > division of comps ——> choose comp types ( function comp or class comp ) ——-> dev a comp : (state) , structure , (styles) , (event)——> one by one dev a comp like last step

note: in React, event is just a fn / callback fn passed through a prop of cur comp----- that is , there’s no event but only props in React in terms of syntax formality , so that a comp’s interface is only consisting of props , so that to register an event is to register a prop (whose type constrained as a fn ), and to handle an event is to pass a fn / callback fn as prop.

note: so , in React, props is the unique interface through which a comp communicates with the external world

note: in React , in a node in JSX or TSX, expression could only be put in { }

// ChessComp : to display a chess , u need to tell me what type of the chess —— that is, a prop ; if u use TS , u yet need to constrain the type of props

// ChessComp : ChessComp says, “ i know here needs an event handler (Say, here sth will happen definitely —— when user click me , here will trigger an event ) , but i am just a chess display comp , and hence i don’t know how to handle this event ( i don’t know what to do), so that i need to emit an event , that is, to define/ register one more prop that is contained as a fn/callback fn. And usually the fn (prop) is optional : only if u has passed a fn / callback fn , i will execute the fn “

//ChessComp: it’s no state , that is , a stateless comp, so it should be defined as a function comp.

// ChesssBoardComp : to display a chess board , u need to tell me an array of chess——-that is , a prop ; if u use TS , u yet need to constrain the type of props

// ChesssBoardComp : ChesssBoardComp says, “ i know here needs an event handler, but i also don’t know to to handle this event , so i need to emit an event , that is , to defined/register one more prop that is constrained as a fn/callback fn. And usually the fn (prop) is optional : only if u has passed a fn / callback fn , i will execute the fn ”

// ChesssBoardComp : it’s no state , that is , a stateless comp, so it should be defined as a function comp.

roadmap : how to choose the category of a comp when intend to target function comp : no state of self ——> so just display ——> so it’s a display comp ——> so it should be defined as a function comp

to define a function comp : to define (props), structure , (styles) ,and (action : just emit event)

//GameComp: to take charge of providing and maintaining state/data (what data & how data to change ) in this game. And hence it’s a stateful comp , namely , a container comp so that it should be defined as a class comp.

raodmap : how to choose the category of a comp when intend to target class comp: having state of self ----> so have to / so must involve processing data———> so it’s a container comp ——> so it should be defined as a class comp

to define a class comp : to define state, (props) , (structure) , (styles) , (action: provide and maintain state/data )

define type IProps ; then constrain the type of the props of the comp as IProps ——that is , use the defined type IProps

note: since React uses function comp and class comp , we write React code is exactly the same way of writing JS code.

`me`

narrow definition of comp: any composable code snippet that returns UI usually with only one root node.

generic definition of comp : any composable code snippet

```



couple    ====  connection   /  relation


note :     the height  and  width of a chess should be  defined as   props   ,  then  set up   a chess ’s width and height  dynamically  through style property of the element.


note:  in  React  , a  list is directly  rendered  as the content of a node




note:  if u  intend to  set up  default value for a prop ,  u aught to  manifest  the prop  as  optional  with a notation “?”



note:  about ES modules , if u want to use basic export of a module  ,  the export statement must use  a variable statement  or  fn statement  , however , u can still use  like so :

  export  { variable1, variable2,…}

 to  export  one or more variables.

in React,  how to set up default value for props
note :  in React,  how to set up default prop value for  a comp ?

        1st , u need to  add on   a type  constraint  (React.FC<IProps>)  to   cur comp  (a fn or  class)

         2nd,   set up  the default value for  one particular prop , or set up  the default values for more  specific props.

               NameComp.defaultPorps =  {

                         isGameOver: false
                    }


          export  {      NameComp       }




non-empty asserting

for some reason,   as to   a data  whose tooltip shows  that  the data’s type includes  scenarios of empty such as  undefined  or null ,   we can manually forcedly tell  TS to ignore  the  scenario of empty  of the type of the data   by using     non-empty  asserting   , which is also a type asserting

  eg.

  const isGameOver  =   props.isGameOver!


 or


 const isGameOver  =   props.isGameOver as  boolean



encapsulate  game init fn

encapsulate   a fn  named init  responsible  for game data init task , which can make code reusable to reduce code verbose   ,  and   call  init  fn  in   comp lifecycle  hook fn   componentDidMount  (when cur comp ins has been inserted into page, run this lifecycle fn )



dev  GameComp    （  a container  comp :   to think about    providing what data and how to change them）

1. put down  cheeses   one by one

2. every time i  put down  a chess ,  it  is possible to change the game status





this is the thing.   a fn  or a class  is just like a ppl  dealing with things  based on logic  like   sometimes  u have to  give me  dispensable  info / data    as  input  ,  and so then i could possibly be able to  give back a proper result / data    as output  after  operating .    it’s not gut feeling, but instead every step of action is  on the basis of logic.



note:   in React,   the fn  setState is  async , that is ,    not a sync fn.    it will start being executed after all the sync code ( code in main execution / call stack ) executed ——— like ,   having planned  well to change / reassign the values of specific states  ( having   snapshotted the spot of input data and knowing how to change the states)    but not yet  started  realizing the plan. (that is  a closure  and meanwhile is an async callback fn  as well ) ——— just like Vue,  states will going to be updated  asynchronously ——— in React, fn setState  ’s executing will be added to  event queue.   ———   since  states will be going to be  updated asynchronously ,   u  can not  one hundred percent make sure  / guarantee  the
most-newly-updated state  is  available  as input  or param for the fn (u call in setState)   while the  fn  is being executed , ———— and hence , u should NOT directly  use  the about-to-update  state   , u better use  the about-to-be-used-to-assign-state   value   as  the input or param of the fn  ( u call  in setState)  about to be invoked ——— because it’s safe to make sure  the fn  (u call in setState)  use the most-newly-updated state

interface IState {
      cheeses: ChessType[]
      gameStatus: GameStatus
       nextStatus:   GameStatus.red | GameStatus.blaack
}
export  class GameComp  extends React.Component<{},IState,SS>{


  //initialize  state  (manually)
 state:IState = {
     chesses:[]
     gameStatus:GameStatus.gaming
     nextStatus:GameStatus.black
  }

// operation :     initially assigning :    init  game  data / states

init(){
     //intermidate computing :  provide  about-to-be-used-as-value-to-assign-state    value  for  state  chesses
    const    chesses  =    …….
   // opeartion
    this.setState({
       chesses,
      gameStatus:  GameStatus.gaming ,
      nextStatus: GameStatus.black
      })
}
// comp lifecycle hook fn  : when  comp in  inserted into parent node ( which amounts to when comp ins  inserted to page)
componentDidMount(){
       this.init()
}

   // operation:       reassigning :    update /change/ maintain game data /states    :   chesses  ,  gameStatus
   onClick(index){
     //intermediate computing :  provide  about-to-be-used-as-value-to-assign-state    value  for  state  chesses

    const    chesses  =   ….

      // operation
    setState(prevState=>{

                  return {
                      chesses,
                      nextStatus :  this.state.nextStatus === GameStatus.red ? GameStatus.black : GameStatus.red ,
                    gameStatus:  getGameStatus(chesses)
                   }


          })


 }

  // intermediate  computing  fn  :   provide about-to-be-used-as-value-to-assign-state    value  for  state   gameStatus
  function  getStatus(chesses:chessType[]):GameStatus{



 }


}



how to design comp
 note :  so , in React,  when  design/compose  display comp / a  function  comp  , just  think about  props ( type constraints,  maybe setting specific  props default value )  and when  design/ author  container comp / a  class  comp  , just  consider  (props)  , state  ( type constraints,   provide   ( initially assigning)  &   maintain (midway computing , reassigning  )）


——  in brief   ,  when   design / compose  a   function comp  : just  consider  props  (type constraints)

                           when   design / compose  a   class comp :   just  consider    state  (type constraints    ,  assigning ,   intermediate  computing ,   reassigning ）


———  in brief,  when  design / compose a comp  , we r programming facing or targeting   data   , that is , ( props , state  )



note:  A fn or a class is just like a human dealing with things based on logic, like sometimes you have to give me dispensable information or data as input,  and so then I could possibly be able to give back a proper result or data as output after handling. It’s not a gut feeling, but instead every step of action is based on logic.



note:   a function (like getStatus) says :   if i  was not given   enough or more detail   info , i may also computing out the result ,  but  it may lead to wasting my efficiency


note:   for a fn,    author its function / algorithm / task / functionality /computing    :       the approach is ,    first lay out  the general mindset/mentality/ roadmap , that is ,  the general  solution  to   the design  of  the  implementation of  the  functionality     ;    when it comes to  each step  ,  then when dive into it,  it can involve knowledge  of/about logic (judgement )  and even  mathematics  (caculate)


note： over the course  of  writing a  display comp ,   we can don’t care about  styles setups / configuration  (but can just give classnames to nodes ) , before  completing   developing a display comp  , and put styles setups / configuration  in the last step to do .



note:  in Reach ,  just like in Vue,    change of  data  (props & state)   will lead to    update view layer ( re-render  cur comp ins)


 ever :  React  without TS  ,  there r common issues such as  one prop  of props  not passing ,  the type of  some  prop  of  props  doesn’t match the type required or intended  , which  consume  plenty  of debug time  , which  we don’t desire.


now:  React with TS,   those common issues mentioned above  r perfectly solved  by making the most of TS’s  type sys.


```
