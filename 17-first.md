---
layout: default
title: Blogging Like a Hacker
---

###   react-state

        在index.js中：

            import React from 'react';
            import ReactDOM from 'react-dom';

            import App from './App';

            ReactDOM.render(
                <div>
                  <App />
               </div>,
              document.getElementById("app")
            )


　　　　　在App.js中：

            import React from 'react';

            class App extends React.Component{
              render(){
                let num=0;
                setInterval(function(){

                })
                return (
                  <div>
                    app
                  </div>
                )
              }
            }
            export default App;

            <!-- import React from 'react';

            class App extends React.Component{
              constructor(){
                super();
                this.state={
                  num:0
                }
              }
              handleClick(){
                console.log(this)
              }
              render(){
                return (
                  <div>
                    数字是：{this.state.num}
                    <button onClick={this.handleClick.bind(this)}>+1</button>
                  </div>
                )
              }
            }
            export default App; -->


            import React from 'react';

            class App extends React.Component{
              constructor(){
                super();
                this.state={
                  num:0
                }
              }
              handleClick(){
                this.setState({num:this.state.num+1})
              }
              render(){
                return (
                  <div>
                    数字是：{this.state.num}
                    <button onClick={this.handleClick.bind(this)}>+1</button>
                  </div>
                )
              }
            }
            export default App;

            <!-- import React from 'react';

            class App extends React.Component{
              constructor(){
                super();
                this.state={
                  num:0
                }
              }
              handleAdd(){
                this.setState({num:this.state.num+1})
              }
              handleCut(){
                this.setState({num:this.state.num-1})
              }
              render(){
                return (
                  <div>
                    数字是：{this.state.num}
                    <button onClick={this.handleAdd.bind(this)}>+1</button>
                    <button onClick={this.handleCut.bind(this)}>-1</button>
                  </div>
                )
              }
            }

            export default App; -->

            import React from 'react';

            class App extends React.Component{
              constructor(){
                super();
                this.state={
                  num:0,
                  show:false
                }
              }
              handleCut(){
                this.setState({show:!this.state.show})
              }
              render(){
                return (
                  <div>
                    数字是：{this.state.num}
                    <button onClick={this.handleCut.bind(this)}>show</button>
                  <p>你现在显示吗？{this.state.show ? "显示":"不显示"}</p>
                  </div>
                )
              }
            }
            export default App;


            <!-- import React from 'react';

            class App extends React.Component{
              constructor(){
                super();
                this.state={
                  num:0,
                  show:false
                }
              }
              handleAdd(){
                            this.setState({num:this.state.num+1})
                          }
              handleCut(){
                this.setState({
                  num:this.state.num-1,
                  show:!this.state.show
                })
              }
              render(){
                return (
                  <div>
                    数字是：{this.state.num}
                    <button onClick={this.handleAdd.bind(this)}>+1</button>
                    <button onClick={this.handleCut.bind(this)}>{this.state.show ?'隐藏':'显示'}</button>
                  <p style={{display:this.state.show ? "block":"none"}}>你现在显示吗？</p>
                  </div>
                )
              }
            }

            export default App; -->

          let data=[
            "第一条信息",
            "第二条信息",
            <p>aaa</p>,//报错，少插件
            "hello world",
            "第四条信息"
          ]
           *  可以加文本，标签，不能加｛aa:"aaa"｝

           let content=this.state.text.map(
              item=><p>今天的消息是：{item}</p>
           )
           *  map返回，forEach不返回

          item=><div　key={Math.random()}><p>今天的消息是：{item}</p><button>删除</button></div>
           *  数组必须加key,防止报错

　　　　　　定义state
          class App extends React.Component{
             constructor(){
               super();
               this.state={
                  属性名：属性值
               }
             }
             render(){
                return (
                  <div>
                    {this.state.属性值}
                  </div>
                )
            　}
            ｝

            *  随机切换文本
            import React from 'react';

           let data=['白菜','胡萝卜','油菜','空心菜','卷心菜','豆芽']
           class EatWhat extends React.Component{
             constructor(){
               super();
               this.state={
                  start:false,
                  data,
                  text:""
               }
             }
            select(){
               this.setState({text:this.state.data[Math.floor(Math.random()*this.state.data.length)]})
             }
             handleClick(){
               if(this.state.start){
                 clearInterval(this.interval);
                  this.setState({start:false})
               }else{
                 this.interval=setInterval(()=>this.select(), 1000);
                 this.setState({start:true})
               }

             }
             render(){
               return (
                 <div>
                   <p style={{color:"red"}}>我猜你想吃：{this.state.text}</p>
                 　<button　onClick={this.handleClick.bind(this)}>{this.state.start?"停止":"开始"}</button>
                 </div>
               )
             }
           }

           export default EatWhat;
