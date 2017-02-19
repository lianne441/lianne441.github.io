---
layout: default
title: Blogging Like a Hacker
---

###  es6语法


     let和const块级作用域

     let 只是在对应的作用域中起作用，往下的作用域
     例如：
    　console.log(a);
     let a= 2;//undifined　

     let 会报错重复声明
     例：
　　　let a=5;
　　　let a=6;
    　正确：
        let a=５；
        ｛
　　　　　　let a=6;
        ｝

     const a=5;a=10

    let声明多变量
     let [a,b,c]=['aaa',345,456]
     console.log(a,b,c)
     let [a,[b,c]]=['aaa',[345,345]]
     console.log(a,b,c)

     var [x,y]=fun();
     function fun(){
       return [5,7]
     }
     console.log(x,y)

     let res={
       a:5,
       b:4,
       c:6
     }
     let {a,c}=res;
     console.log(a,c)

     let [a,b,c,d,e,f]='hello';
     console.log(a+'\n',b+"\n",c+"\n",d+"\n"+e)

     var  a=x=>x+5;
     console.log(a(8))；
     相当于：
     var a = function a(x) { return x + 5;};
     console.log(a(7));

     多个加（）
     var b = (x,y) =>x+y;
     console.log(b(3,2))
     多条语句用大括号包裹，小括号返回对象
     箭头函数this没有自己的指向
     var  a = (name,age)=> ({name:name,age:age});
     console.log(a("suiliyan",2))

　　
    var obj={
      say:function(){
      　　setTimeout(function(){
            console.log(1)
        },1000)
        return  666;
      }
    }
    console.log(obj.say())

    let obg={
      a:“ssss”,
      say(){
        console.log("es6")
      }
    }
    console.log(obg.say())

    function add(x=5,y=10){
      return  x+y;
    }
    console.log(add(500,600))

    var c=()=>{
      console.log('aaa');
      alert('bbb');
      return 3;
    }
    console.log(c())

    let age=10;
    let name="suiliyan"

    console.log(`姓名是${name}的年龄是${age}岁`)

　　剩余函数
    function restFunc(a,...rest){
      console.log(a)
      console.log(rest)
    }
    restFunc(1,2,3,4,5)

    // function restFunc(...rest){
    //   console.log(rest)
    // }
    // restFunc(1,2,3,4,5)

　　reduce函数
    function add(...x){
      return x.reduce((m,n)=>m+n);

    }
    console.log(add(1,2,3))
    console.log(add(1,2,3,4,100))

    回调函数
    function a(cb){
      cb("aaa");
    }

    a(function(str){
      alert(str)
    })


　　拓展函数

    var people=['zf','John','Sherlock'];

    function sayHello(people1,people2,people3){
        console.log(`Hello ${people1},${people2},${people3}`);
    }

    //但是我们将一个数组以拓展参数的形式传递，它能很好地映射到每个单独的参数

    sayHello(...people);//输出：Hello zf,John,Sherlock
　　或者：
    var people=['zf','John','Sherlock'];

    function sayHello(people1,people2,people3){
        console.log(`Hello ${people1},${people2},${people3}`);
    }
    //但是我们将一个数组以拓展参数的形式传递，它能很好地映射到每个单独的参数

    sayHello(people,666,888);//输出：Hello zf,John,Sherlock,666,888

    let arr1=[1,3,5]
    let arr2=[199,23]
    let arr3=[...arr1,...arr2]
    console.log(arr3)

　　map函数

    let arr=[1,2,3];
    let newArr=arr.map(function(currentValue, index, array){
      　console.log(currentValue, index, array);
       return currentValue+10;
    })

    console.log(newArr)

    forEach遍例

　　let arr=[4,5,6];
   arr.foreach(function(currentValue, index, array){
      console.log(currentValue, index, array);
   })

   let arr4=[4,5,6];
    arr4.forEach(item => console.log(item+10))
    //  arr4.foreach(function(currentValue, index, array){
    //     console.log(currentValue, index, array);
    //
    //  })

　　 filter过滤

    let arr5=[4,6,8,9];
     var results=arr5.filter(function(item, index, array){
        console.log(item, index,  array);
        return item >8;
       })
      console.log("results======",results)

    Class, extends, super 类的支持

      function Point(x,y){
        this.x = x;
        this.y = y;
      }
      Point.prototype.toString = function () {
        return '(' + this.x + ', ' + this.y + ')';
      }
      var point = new Point(6,3);
      console.log(point.x)
      console.log(point.y)
      console.log(point.toString());//(6,3)

      function Point(x,y){
        this.x = x;
        this.y = y;
      }
      Point.prototype.toString = function () {
        return `(${this.x},${this.y})`;
      }
      Point.prototype.name="suiliyan"

      function  Hello(){
        this.toString =  function(){
          return "hello say";
        }
      }
      let xx=new Point(5,6);
      Hello.prototype=xx;

      var p=new Hello();

      console.log(p.toString())
      console.log(p.name)

　　　类中只能写构造函数块（方法）
      class Point{
        constructor(x,y){
          console.log("我是自动执行的");
          this.x=x;
          this.y=y;
        }
      }
      var p=new Point(5,6);
      console.log(p.x,p.y)

      class Point{
        constructor(x,y){
          console.log("我是自动执行的");
          this.x=x;
          this.y=y;
        }
        toString(){
          return this.x;
        }
      }
      var p=new Point(5,6);
      console.log(p.x,p.y)
      console.log(p.toString())

      class Point{
        constructor(x,y){
          console.log("我是自动执行的");
          this.x=x;
          this.y=y;
        }
        toString(){
          return `point tostring`;
        }
        say(){

        }
      }
      class Hello extends Point{
        say(){
          return  `hello say`
        }
      }
      var p=new Hello();

      console.log(p.say())
      console.log(p.toString())

      class Point{
        constructor(){
          console.log("我是自动执行的");
          this.x='jhjh';
          this.y='hkhjkhk';
        }
        toString(){
          return `point tostring`;
        }
      }
      class Hello extends Point{
        constructor(c){
          super();
          this.c=c;
        }
        say(){
          return  this.x;
        }
      }
      var p=new Hello(4);
      console.log(p.say())
      console.log(p.c)

      class Father{
        render(){
          throw  new Error("子类必须实现")
        }
        _render(){
          return(`
             <ul>
               ${this.render()}
             </ul>
            `)
        }
      }
      class Son extends Father{
         render(){
           return(`
              <li>1234546</li>
             `)
         }
      }
      document.getElementById('app').innerHTML=new Son()._render();

      在demo.js中：
        let a=10;

        function aa(x){
          console.log("aa");
          return x*8
        }

        class Father{
          render(){
            throw  new Error("子类必须实现")
          }
          _render(){
            return(`
               <ul>
                 ${this.render()}
               </ul>
              `)
          }
        }
        export {a,aa,Father}//命名导出

      index.js中：
        import {a,Father,aa} from './demo';
        console.log(a)//10
        console.log(aa(6))//aa 48
        class Son extends Father{
               render(){
                 return(`
                    <li>1234546</li>
                   `)
               }
            }
        document.getElementById('app').innerHTML=new Son()._render();//.123456

      demo.js中:
        function aa(x){
          console.log("aa");
          return x*8
        }
       export default aa;

     index.js中：
       import cc from './demo';
       console.log(cc(3))//cc可以是任意名称，输出结果为：aa 24
