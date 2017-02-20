---
layout: default
title: Blogging Like a Hacker
---


###   props


      index.js中：

          import React from 'react';
          import ReactDOM from 'react-dom';


          import App from './App';
          import  './main.css';

          ReactDOM.render(
              <div>
                <App />
             </div>,
            document.getElementById("app")
          )

　　　　cards.js中：

          import React from 'react';

          class Card extends React.Component{
            render(){
              return(
                <div className='card'>
                  <div className='card-index'>{this.props.index}</div>
                  <div className='card-info'>
                    <h3>{this.props.title}</h3>
                    <p>{this.props.date}</p>
                  </div>
                </div>
              )
            }
          }
          Card.defaultProps={
            index:"1",
            title:"这是默认标题",
            date:"2017.2.20"

          }
          export default Card;

　　　　Btn.js中：

            import React from 'react';


            class Btn extends React.Component{
              render(){
                let styles={
                  padding:`${this.props.padd}px`,
                  backgroundColor:this.props.bg,
                  border:'10px solid red',
                  color:'#fff',
                  fontSize:"25px"
                }
                return(
                  <button style={styles}>
                     {this.props.title}
                  </button>
                )
              }
            }
            Btn.defaultProps={
              title:'defaultTitle',
              bg:'#00bcd4',
              padd:10
            };
            export default Btn;

　　　　　main.css中：

              *{
                margin: 0;
                padding: 0;
                box-sizing: border-box;
              }
              .card{
                width: 100%;
                max-width: 760px;
                margin: 0 auto;
                margin-top: 10px;
                height: 80px;
                box-shadow: rgba(0, 0, 0, 0.2) 0px 1px 6px,rgba(0, 0, 0, 0.2) 0px 1px 4px;
                overflow: hidden;
              }
              .card-index{
                width: 10%;
                height: 80px;
                float: left;
                background-color: red;
                text-align: center;
                font-size: 20px;
              }
              .card-info{
                width: 90%;
                height: 80px;
                float: right;
                background-color: gray;

              }

　　　　　App.js中：

            import React from 'react';

            // import Btn from './Btn';
            import Card from './Card';
            import  './main.css';

            let data=[
              {index:1,title:'标题一',date:'2017.1.1'},
              {index:2,title:'标题二',date:'2017.1.2'},
              {index:3,title:'标题三',date:'2017.1.3'}
            ]
            class App extends React.Component{
              constructor(){
                super();
                this.state={data:data}
              }
              render(){
                return(
                  <div>
                    {this.state.data.map(item =><Card key={Math.random()} title={item.title} index={item.index} date={item.date} />)}
                  </div>
                )
              }
            }
            export default App;
