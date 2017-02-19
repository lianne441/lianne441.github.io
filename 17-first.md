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

　　　　　　定义state
             constructor(){
               super();
               this.state={
                 
               }
             }
