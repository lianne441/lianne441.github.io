---
layout: default
title: Blogging Like a Hacker
---


###   React

      import React from 'react';
      import ReactDOM from 'react-dom';

      ReactDOM.render(
          <div>
              <h1>fhggg</h1>
          </div>,
          document.getElementById("app")
      )
      // ReactDOM.render(
      //   <div>hello react</div>,
      //   document.getElementById("app")
      // )

      1. 每个标签必须关闭，如：img

      import React from 'react';
      import ReactDOM from 'react-dom';
      let a=  <div>
                <h1>fhggg</h1>
                <img src="" />
              </div>
      ReactDOM.render(
        a  ,document.getElementById("app")
      )

      2. 注释的写法：｛/* commits */｝

      3. jsx中嵌入变量｛obg｝

      4. class 写为　className,tabindex 变为 tabIndex,for 写为　htmlfor

      5.jsx中语法编译，用react.createElement()这个方法

　　　

     index.js中：
     let name="suiliyan";
    let age=2;
    let male=0;
    let　obg={name:"aaa"}
    function add(){
      return 5+8
    }

    let a=  <div>
             <h1>fhggg</h1>
             {/* 这是注释 */}
             <h1>{name+"haha"}</h1>
             <h1>年龄：{age*5}</h1>
             <h1 className={male?"aaa":"bbb"}>性别：{male?'男':'女'}</h1>
             {/* 三目运算，１或０　真＝男，假＝女*/}
             <h1>{obg.name}</h1>
             <h1>{add()}</h1>
         </div>


　　　　　

      组件component(3种方式)　首字母大写
      　１.var Hello=react.createclass({}) es5写法，不用

        (１）function Greeting(){
              return <h1>hello</h1>;
         }
         ReactDOM.render(
         <Greeting />,
           document.getElementById("app")
         )

       （２） var Greeting = React.createClass({
             render:function(){
               return <h1>hello</h1>;
             }
          })

          ReactDOM.render(
          <Greeting />,
            document.getElementById("app")
          )
        2.function Hello(){
          return(<h1>aaa</h1>)
        }使用时<hello />

        import React from 'react';
        import ReactDOM from 'react-dom';

        function Hello(){
          return (
             <div>
               <h1>asdfg</h1>
               <h1>asdfg</h1>
               <div>
                 <h1>asdfg</h1>
                 <h1>asdfg</h1>
               </div>
             </div>
          )
        }//组件
        let a=<h1>Hello</h1> //变量a
        ReactDOM.render(
        <Hello />,
          document.getElementById("app")
        )
        3.
