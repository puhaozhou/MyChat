<template>
    <div id="chat">  
        <div id="title">
            <span class="glyphicon glyphicon-chevron-left"></span>
            <span id="friend_name">{{data.friend}}</span>
        </div>    
        <div id="content">
           <div v-for="row in message_data">
               <div :class="row.style">
               <label>{{row.userName}}</label>
               <span>{{row.text}}</span>
               </div>
           </div>
        </div>
        <div id="edit">
        <!-- <img src="1.jpg" id="Img"> -->
        <textarea name="" id="txt" wrap="virtual"></textarea>
        <input type="button" name="" value="send" id="btn" @click="sendMessage()">
        </div>
    </div>
</template>
<script>
export default {
    name:"Chat",
    props:{},
    computed:{
        message_data(){
          var messages = this.data.messages;
          messages.map(function(i){
            if(i.userName == "me"){
              i.style = "btalk"
            } else {
              i.style = "atalk"
            }
          });
          return messages;
        }
    },
    data(){
       return {
           //实际为通过api接口获取数据
           data:{
               friend:"John",
               messages:[
               {userName:"me", text:"hello"},
               {userName:"John", text:"hi"},
               {userName:"me", text:"glad to see u"},
               {userName:"John", text:"How r u today?"},
               {userName:"me", text:"I'm doing well"}]
           }         
       }
    },
    methods:{
        sendMessage(){
            var messages = this.data.messages;
            var text = $("#txt").val();
            var my_message = {};
            my_message.userName = "me";
            my_message.text = text;
            messages.push(my_message);//实际为发送到api接口
            //以下代码只是为了观测效果
            setTimeout(function(){
               var others_message = {};
               others_message.userName = "John";
               others_message.text = "test";
               messages.push(others_message);
            },"1000");          
        }
    }
}
</script>
<style>
        html,body{
            height:100%; 
            width:100%;
        }
        .glyphicon.glyphicon-chevron-left{
            width: 40%;
            margin: 0 auto;
            position: relative;
            top: 50%; 
            transform: translateY(-50%);
            float:left;
        }
        #friend_name{
            height:100%;
            width:80%;
            font-size:xx-large;
            text-align: center;
            color:black;
            font-weight: bolder;
        }
        #chat,#app{
            height:100%;
            width:100%;
            margin:0;
            background:#f9f9f9;
        }
        #title{
            width:100%;
            height:5%;
            background: #ece7e766;
        }
        #content{
            width:100%;
            height:85%;
            background:#fff;
            margin:0;
            overflow:auto;
        }
        #edit{
            background: #ece7e766;
            height: 10%;
            width:100%;
            display:inline-block
        }
        #txt{
            /* margin: 2.5% 0 0 5%; */
            margin: 0 auto;
            margin-left:5%;
            border:1px solid #ccc;
            /* float: left; */
            width: 70%;
            height: 50%;
            overflow: hidden;
            resize:none;
            position: relative;
            top: 50%; 
            transform: translateY(-50%);
        }
        #btn{
            float:right;
            margin-right: 10px;
            /* margin-top: 20px; */
            width: 10%;
            height: 50%;
            position: relative;
            top: 50%; /*偏移*/
            transform: translateY(-50%);
        }
        #Img{
            width: 10%;
            height: 50%;
            /* margin-top: 20px; */
            margin-left: 10px;
            float:left;
            background-color:black;
            position: relative;
            top: 50%; /*偏移*/
            transform: translateY(-50%);
        }
        .atalk{
           margin:10px;
        }
        .atalk label{
            float: left;
        }
        .atalk span{
            margin-left: 10px;
            display:inline-block;
            background:#0181cc;
            border-radius:10px;
            color:#fff;
            padding:5px 10px;
            max-width:70%;
            word-wrap: break-word;
            word-break: normal;
        }
        .btalk{
            margin:10px;
            text-align:right;
        }
        .btalk label{
            float: right;
        }
        .btalk span{
            margin-right: 10px;
            display:inline-block;
            background:#ef8201;
            border-radius:10px;
            color:#fff;
            padding:5px 10px;
            max-width:70%;
            word-wrap: break-word;
            word-break: normal;
        }
</style>

