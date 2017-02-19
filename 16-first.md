---
layout: default
title: Blogging Like a Hacker
---

###   构架

      １．新建一个Header.js:

            import React from 'react';

            import Logo from './Logo';
            import SignIn from './SignIn';

            class Header extends React.Component{
                render(){
                    return (
                        <div>
                          <Logo />
                          <SignIn />
                        </div>
                    )
                }
            }

            export default Header;

          新建一个Logo.js:

            import React from 'react';

            class Logo extends React.Component{
                render(){
                  let styles={width:"150px",border:"3px solid #ccc",borderRadius:"8px"}
                  return (
                    <img src="https://www.baidu.com/img/bd_logo1.png" style={styles}/>
                  )
                }
              }
            export default Logo;

            <!-- import React from 'react';
            import img from "./images/a.jpg";

            class Logo extends React.Component{
                render(){
                  let styles={width:"150px",border:"3px solid #ccc",borderRadius:"8px"}
                  return (
                    <img src={img} style={styles}/>
                  )
                }
              }

            export default Logo; -->

            import React from 'react';

            class Logo extends React.Component{
                render(){
                  let styles={
                    fontSize:"20px",
                    width:"100%",
                    height:"100px",
                    display:"block",
                    backgroundColor:"black",
                    color:"white"
                  }
                  return (
                  <span style={styles} className="logo">project name</span>
                  )
                }
              }

            export default Logo;

          新建一个SignIn.js:

            import React from 'react';

            class SignIn extends React.Component{
              getStyles(){
                return {
                  float:"left",border:"1px solid #ccc"
                }
              }

              render(){
                  let styles={
                    leftBtn:{
                      background:"red"
                    },
                    rightBtn:{
                        background:"blue"
                    }
                  }
                  return (
                    <div style={this.getStyles()}>
                      <button style={styles.leftBtn} className="aaa">登陆</button>
                      <button style={styles.rightBtn}>注册</button>
                    </div>
                  )
              }
            }
            export default SignIn;

          新建一个Banner.js:

            import React from 'react';

            class Banner extends React.Component{
              render(){
                return (
                  <div>
                    我是banner
                  </div>
                )
              }
            }

            export default Banner;

          新建一个Footer.js:

            import React from 'react';

            class Footer extends React.Component{
              render(){
                return (
                  <div>
                    我是footer
                  </div>
                )
              }
            }

            export default Footer;

          新建一个App.js:

              import React from 'react';

              import Header from './Header';
              import Footer from './Footer';
              import Banner from './Banner';

              class App extends React.Component{
              render(){
                return (
                  <div>
                    <Header />
                    <Banner />
                    <Footer />
                  </div>
                )
              }
              }

              export default App;


          index.js中：

            import React from 'react';
            import ReactDOM from 'react-dom';
            import App from './App';

            ReactDOM.render(
            <App />,
              document.getElementById("app")
            )

             webpack.config.js中：

             module.exports = {
                  entry: './src/index.js',
                  output: {
                      path: 'build',
                      filename: 'bundle.js',
                      publicPath: "build/"
                  },
                  devtool:"eval",
                  resolve:{
                    extensions:["",".js",'.jsx',".css",".jpg"]
                  }
                  module: {
                      rules: [
                        { test: /\.js$/, exclude: /node_modules/, use: "babel-loader" },
                        {test: /\.css/,use:['style-loader',"css-loader"]},
                        {test: /\.(jpe?g|png)$/,loader:"file-loader"}
                      ]
                  }
              };
