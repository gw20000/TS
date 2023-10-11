TS-2-scaffold ts dev env in node env

BTW: if want to scaffold ts（+Vue or + React） dev env in BS env , u need combine webpack to scaffold a project

@types
@types is rolled out officially by Microsoft
@types is a lib consisting of types description/ definition/ constraints for a variety of JS code , such as node, jQuery, axios.

@types/node , @types/jquery , @types/axios

npm i -D @types/node

use 3rd party libs to concise ts compiling and executing flow , since it’s a bit tedious

1.  ts-node : designed to complete compiling TS code and then subsequently fulfil executing JS code , both in RAM
    npm i -g ts-node

    ts-node src/index.ts

2.  nodemon: committed to watch files’ change.

    npm i -g nodemon

nodemon —exec ts-node src/index.ts

nodemon -e ts —exec ts-node src/index.ts // confine/ restrict the watching scope by nodemon , which by default watch the whole project directory ’s files’ change ; now we configure its -e option to specify nodemon only watching ts files’ change.

nodemon -w src -e ts —exec ts-node src/index.ts // similar to the above , now configure to watch ts files’ change under src directory only
