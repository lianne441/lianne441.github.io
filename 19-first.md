---
layout: default
title: Blogging Like a Hacker
---


### react
       发送ajax请求的几种方式：
       １．原生　XMLHttpRequest()
       2.jquery
       $.ajax({type:'POST',data:string,success:function(){}})
       3.fetch
       fetch('url').then(res=>res.json()).then(json=>do())
                   .catch(err=>alert('error'))
       4.axios


      <div id=name>数据还没过来呢</div>
      <script src='http://cdn.bootcss.com/jquery/3.1.1/jquery.min.js'></script>
        var ajax=new XMLHttpRequest();
        ajax.onreadystatechange=function(){
        if(ajax.readyState==4 &&　ajax.status==200){
          let data=JSON.parse(ajax.responseText);
           console.log(data);
             document.getElementById('name').innerHTML=data.name;
          }
        }
        ajax.open('GET','https://api.github.com/users/newming',true)
        ajax.send()

    <div id=name>数据还没过来呢</div>
    <div id=img></div>
    <script src='http://cdn.bootcss.com/jquery/3.1.1/jquery.min.js'></script>
    $.ajax({
      type:'Post',
      datatype:'JSON',
      contenttype:'apllication/JSON',
      data:{
         accesstoken:'3f77acb1-d753-4393-b784-44913190e6a8'
      },
      url:'https://api.github.com/users/newming',
      url:'https://cnodejs.org/api/vl/accesstoken',
      }).done(function(data,status){
       console.log(data,status)
       $('#name').html(data,loginname)
       $('#img').append(`<img src='$(data.avatar_url)'>`)

      }).fail(function(xhr,error){
         alert(error)
      })

      <div id=name>数据还没过来呢</div>
      <script src='http://cdn.bootcss.com/jquery/3.1.1/jquery.min.js'></script>
      $.ajax({
         dataType:'jsonp',
         jsonp:'callback',
         url:'https://api.douban.com/v2/book/1220562'
        }).done(function(data,status){
          console.log(data,status)
        }).fail(function(xhr,error){
          alert(error)
        })

        fetch('https://api.github.com/users/newming',{method:'GET'})
             .then(response=>response.json())
             .then(json=>console.log(json))
             .catch(error=>console.log('error====',error))

        fetch('https://cnodejs.org/api/v1/accesstoken',{
            method:'POST',
            headers:{'Content-Type':'application/json'},
            body:JSON.stringify({
              accesstoken:'3f77acb1-d753-4393-b784-44913190e6a8'
               })
             })
          .then(res=>res.json())
           .then(json=>console.log(json))

       new Promise(function(resolve,reject){
          console.log('run');
          setTimeout(function(){
           reject()
           },3000)

      }).then(function(){
         console.log('thing.then()...')
      }).catch(function(){
       console.log('thing.catch()...')
     })

     <div id=name>数据还没过来呢</div>
     <script src="https://unpkg.com/axios/dist/axios.min.js"></script>
     axios.get('https://api.github.com/users/newming')
           .then(res=>console.log(res.data))
           .catch(error=>console.log(error));

     <div id=name>数据还没过来呢</div>
     <script src="https://unpkg.com/axios/dist/axios.min.js"></script>
     axios.post('https://cnodejs.org/api/v1/accesstoken',{
          accesstoken:'3f77acb1-d753-4393-b784-44913190e6a8'
        }).then(res=>console.log(res.data)).catch(err=>console.log(err))
