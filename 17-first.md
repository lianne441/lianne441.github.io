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

           SelectBar.js中：

                import React from 'react';
                import Tab1 from './Tab1';
                import Tab2 from './Tab2';

                class SelectBar extends React.Component{
                  constructor(){
                    super();
                    this.state={
                       show:0
                    }
                  }

                  handleClick(num){
                    console.log(num)
                    this.setState({show:num})
                  }

                  render(){
                    return (
                      <div>
                        <button onClick={this.handleClick.bind(this,1)}>选项卡一</button>
                        <button onClick={this.handleClick.bind(this,2)}>选项卡二</button>
                        <button onClick={this.handleClick.bind(this,3)}>选项卡三</button>
                        {this.state.show===1? <Tab1 />:
                          this.state.show===2?<Tab2 />:"选项卡三"
                        }
                      </div>
                    )
                  }
                }

                export default SelectBar;

                Tab1.js中：

                    import React from 'react';

                    class Tab1 extends React.Component{

                      render(){

                        return (
                          <div>
                            <p>商品名称：电脑</p>
                            <p>商品名称：电脑</p>
                            <p>商品名称：电脑</p>
                            <p>商品名称：电脑</p>
                            <p>商品名称：电脑</p>
                          </div>
                        )
                      }
                    }
                    export default Tab1;

                Tab2.js中：

                    import React from 'react';

                    class Tab2 extends React.Component{

                      render(){
                        return (
                          <div>
                            <p>评论</p>
                            <p>评论</p>
                            <p>评论</p>
                            <p>评论</p>
                            <p>评论</p>
                          </div>
                        )
                      }
                    }

                    export default Tab2;
　　　　　　　　　

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

　　　　　　　EatWhat.js中：

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
                    this.interval=setInterval(()=>this.select(), 500);
                    this.setState({start:true})
                  }

                }
                render(){
                  return (
                    <div style={{width:"100%",marginLeft:"500px",marginTop:"200px"}}>
                      <p style={{color:"red",fontSize:"20px"}}>我猜你想吃：{this.state.text}</p>
                    　<button　onClick={this.handleClick.bind(this)} style={{fontSize:"20px"}}>{this.state.start?"停止":"开始"}</button>
                    </div>
                  )
                }
              }

              export default EatWhat;

　　　　　trans.js中：

            import React from 'react';


            class Trans extends React.Component{
              constructor(){
                super();
                this.state={
                   show:true
                }
              }
              handleClick(){
                this.setState({show:!this.state.show})
              }
              render(){
                let styles={
                  top:this.state.show　?"30%":"5%",
                  height:this.state.show ? "40vh":"5vh"
                }
                return (
                <div className="container" style={styles}>
                   <button onClick={this.handleClick.bind(this)} style={{float:"right",marginRight:"2vh",display:"block"}}>{this.state.show　?"上":"下"}</button>
                   <a style={{marginTop:"10vh",display:"block"}} href="https://www.baidu.com/?tn=02049043_42_pg&ch=6s">博客标题</a><hr />
                   <a>博客标题</a><hr />
                   <a>博客标题</a><hr />
                   <p >blog</p>

                </div>
                )
              }
            }

            export default Trans;

　　　　main.css中：

            *{
              margin: 0;
              padding: 0;
              box-sizing: border-box;
            }
            html,body{
              height: 100%;
            }
            body{
              position:relative;
              background-image: url("http://www.ruanyifeng.com/images_pub/pub_43.jpg");
              background-size: cover;
              background-position: 50% 50%;
            }
            .container{
              position:absolute;
              width: 40%;
              height: 40vh;
              left:50%;
              top:30%;
              background-color: rgba(0, 0, 0, 0.3);
              margin-left: -30%;
              border-radius:5%;
              text-align: center;
              text-decoration: none;
              color:white;
              transition:all 1s ease;
              overflow: hidden;
            }
