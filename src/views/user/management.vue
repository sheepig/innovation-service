<template>
  <div id = 'outline'>
    <!--user profile-->
    <h1 class = 'info'>账号管理</h1>
    <div class = 'modify-zone'>
      <div class = 'profile-wrap'>
        <div id = 'profile'>
          <img :src = 'info.profile'/>
          <div class = 'upload-profile'>
            <p>上传头像</p>
            <input class = 'cover' type = 'file' accept = 'image/*' @change = 'uploadprofile'/>
          </div>
        </div>
        <div id = 'user-name'>
          <input id = 'userName' v-model = 'info.userName'/>
          <button class = 'bin-modify btn-primary'>修改</button>
        </div>

      </div>
    </div>

    <!--user info-->
    <form class = 'modify-zone'>
      <h2>个人信息</h2>
      <p class = 'user-info-item'>
        <label class = 'info-label' for = 'name'>姓名</label>
        <input id = 'name' type = 'text' v-model = 'info.name'/>
      </p>
      <p class = 'user-info-item'>
        <label class = 'info-label'>性别</label>

        <input id = 'male' type = 'radio' value = '男' v-model = 'info.gender'/>
        <label for = 'male'>男</label>

        <input id = 'female' type = 'radio' value = '女' v-model = 'info.gender'/>
        <label for = 'female'>女</label>
      </p>
      <p class = 'user-info-item'>
        <label class = 'info-label' for = 'domicile'>居住地</label>
        <input id = 'domicile' type = 'text' v-model = 'info.province + info.city'/>
      </p>
      <p class = 'user-info-item'>
        <label class = 'info-label' for = 'school'>学校</label>
        <input id = 'school' type = 'text' v-model = 'info.school'/>
      </p>
      <p class = 'user-info-item'>
        <label class = 'info-label' for = 'profession'>专业</label>
        <input id = 'profession' type = 'text' v-model = 'info.profession'/>
      </p>
      <p class = 'user-info-item'>
        <label class = 'info-label' for = 'mailBox'>邮箱</label>
        <input id = 'mailBox' type = 'text' v-model = 'info.mailBox'/>
      </p>
      <button id = 'info-submit' type = 'submit'>提交</button>
    </form>

    <div class = 'modify-zone'>
      <h2>修改绑定</h2>
      <p class = user-info-item>
        <label class = 'info-label' for = 'phoneNunber'>手机号码</label>
        <input id = 'phoneNunber' type = 'text' v-model = 'info.phoneNumber'/>
        <button class = 'bin-modify btn-primary'>修改</button>
      </p>

    </div>

    <div class = 'modify-zone'>
      <h2>修改密码</h2>
      <p class = 'user-info-item' v-for = 'item in password'>
        <label class = 'info-label' for = 'item.title'>{{ item.title }}</label>
        <input type = 'text' id = 'item.title' v-model = 'item.value'/>
      </p>
    </div>

    <upload-image></upload-image>

  </div>

</template>

<script>
  // import uploadImage from '../../components/uploadImage/uploadImage'
    export default {
      // components: {uploadImage},
      name: "management",
      data() {
        return {
          info: {
            userName:'用户12322',
            profile: 'http://img2.imgtn.bdimg.com/it/u=1710834445,2504986021&fm=27&gp=0.jpg',
            name: '张三',
            gender: '男',
            province: '广东省',
            city: '广州市',
            school: 'scut',
            profession: '信息工程',
            station: '天河区五山街道',
            major: '',
            mailBox: '123456@qq.com',
            phoneNumber: '1456627853'
          },
          password: [
            {
              title: '旧密码',
              value: ''
            },
            {
              title: '新密码',
              value: ''
            },
            {
              title: '确认密码',
              value: ''
            }
          ]
        }
      },
      // component: uploadImage,
      methods: {
        uploadprofile: function(event){
          console.log(event);
          var originPhoto = event.target.files[0];
          var reader = new FileReader();
          var binString = reader.readAsBinaryString(originPhoto);
          reader.onload = function(e){
            console.log(binString);
          }
        }
      }
    }
</script>

<style scoped lang = 'scss'>
  $theme: #3333CC;
  $img-width: 150px;

  #outline{
    border: 1px solid #ddd;
     > h1{
       padding:3px 1em;
       font-weight: normal;
       background-color: #98ccca;
       color: $theme;
     }
  }

  .profile-wrap{
    margin-left: 10%;
    width: 50%;
  }

  #profile{
    margin: 1.5em auto;
    width: 150px;
    height: 150px;
    border-radius: 50%;
    background: #CCC;
    position: relative;
    overflow: hidden;
    img {
      /*border-radius: 50%;*/
      width: $img-width;
    }
  }
  #profile .upload-profile{
    position: absolute;
    width: 100%;
    height: 40%;
    bottom: 0;
    border:0;
    font-size: 1rem;
    text-align: center;
    background-color: rgba(225,225,225,.6);
     .cover{
      position: absolute;
      top: 0;
      left: 0;
      opacity: 0;
      height: 100%;
    }
  }

  .profile-wrap #user-name {
      position: relative;
      margin: 2em auto;
      text-align: center;

      input {
        display: block;
        margin: 0 auto;
        width: 40%;
        text-align: center;
      }
    button{
      position: absolute;
      top: 0;
      right:10%;
    }
  }

  .modify-zone{
    width: 100%;
    margin-bottom: 30px;
    font-size: 1.6em;
    h2{
      padding: 3px 1em;
      font-weight: normal;
      font-size: 1.2em;
      width: 90%;
      border-bottom: 1px solid #ddd;
    }
    .user-info-item {
      padding-left: 1em;
      width: 100%;
       .info-label{
        display: inline-block;
        width: 12%;
      }
      input{
        padding-left: 1em;
        width: 35%;
      }
    }
    .user-info-item #name,
    .user-info-item #male,
    .user-info-item #female {
      width :auto;
    }


   input[type = 'radio'] + label::before{
      content: '\a0';
      display: inline-block;
      margin-right: .4em;
      vertical-align: middle;
      font-size: 1em;
      width: .7em;
      height: .7em;
      border-radius: 50%;
      border: 2px solid #ccc;
     text-indent: .15em;
     line-height: 1;
    }

    input[type = 'radio']:checked + label::before {
      background-color: $theme;
      background-clip: content-box;

    }

    input[type = 'radio']{
      position: absolute;
      clip: rect(0,0,0,0);
    }

  }

  .left-shift {
    margin-left: 15%;
  }

  #info-submit{
    box-sizing: border-box;
    width: 10%;
    margin: 1em 20%;
    background-color: $theme;
    color: #fff;
    border: none;
    box-shadow: 0px 0px 5px #0431ce;
  }

  .btn-primary {
    text-indent: -9999px;
    overflow: hidden;
    border: none;
    width: 4em;
    cursor: pointer;
    outline: none;
    background: url('../../../static/modify.gif') left top no-repeat;
    background-size: contain;
    background-position: center;
  }




</style>
