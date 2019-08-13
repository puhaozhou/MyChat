<template>
    <div id="chat">  
        <div id="title">
            <span class="glyphicon glyphicon-chevron-left"></span>
            <span id="friend_name">{{data.friend}}</span>
        </div>    
        <div id="content">
           <div class="atalk" v-for="row in data.messages">
               <label>{{row.userName}}:</label>
               <span>{{row.text}}</span>
           </div>
        </div>
        <div id="edit">
        <!-- <img src="1.jpg" id="Img"> -->
        <input type="text" name="" id="txt">
        <input type="button" name="" value="发送" id="btn" @click="sendMessage()">
        </div>
    </div>
</template>
<script>
export default {
    name:"Chat",
    props:{},
    computed:{
        isMe(name){
          if(name == "me"){
              return true;
          } else {
              return false;
          }
        }
    },
    data(){
       return {
           data:{
               friend:"John",
               messages:[
               {userName:"me", text:"hello"},
               {userName:"John", text:"hi"},
               {userName:"me", text:"glad to see u"},
               {userName:"John", text:"How r u today?"},
               {userName:"me", text:"I'm doing well"}
           ]}
       }
    },
    methods:{
        sendMessage(){
            var text = $("#txt").val();
            var message = {};
            message.userName = "me";
            message.text = text;
            this.data.messages.push(message);
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
        #txt{
            /* margin: 2.5% 0 0 5%; */
            margin: 0 auto;
            margin-left:5%;
            border:1px solid #ccc;
            /* float: left; */
            width: 70%;
            height: 50%;
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
        #edit{
            background: #ece7e766;
            height: 10%;
            width:100%;
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
        .atalk span{
            display:inline-block;
            background:#0181cc;
            border-radius:10px;
            color:#fff;
            padding:5px 10px;
            max-width:70%;
            word-wrap: break-word;
            word-break: normal;
        }
</style>

