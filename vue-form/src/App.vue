<template>
  <div>
    <ProgressBar></ProgressBar>
    <form v-on:submit.prevent="submitForm"> 
      <div>
        <label for="username">ID : </label>
        <input 
          id="username" 
          type="text" 
          v-model="username" 
          class="username-input"
          v-bind:class="{ 'error' : isError }"
        >
      </div>
       <div>
        <label for="password">PW : </label>
        <input id="password" type="password" v-model="password">
      </div>
      <button v-bind:disabled="!isUsernameValid" type="submit" >로그인</button>
    </form>
    <p v-if="isSuccess">로그인이 되었습니다.</p>
    <!-- <p v-if="isError">올바르지 않은 ID입니다.</p>
    <p v-if="isUsernameValid">이메일 형식이 맞습니다.</p> -->
    <ToastPopup v-bind:open="isSuccess" v-on:close="isSuccess = false"></ToastPopup>
  </div>
</template>

<script>
import ProgressBar from '@/components/ProgressBar.vue';
import ToastPopup from '@/components/ToastPopup.vue';


// 이메일 형식 체크 함수
function validateEmail(email) {
    var re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
    return re.test(String(email).toLowerCase());
}

export default {
  components: {
    ToastPopup,
    ProgressBar
  },
    data() {
      return {
        username: '',
        password: '',
        isError : false,
        isSuccess : false
      };
    },
    computed: {
      isUsernameValid ( ) {
        return validateEmail(this.username);
      }, 
    },
    methods: {
      submitForm() {
        // event.preventDefault(); form->submit.prevent로 사용 가능
        console.log('로그인');
        // axios
        //   .post()
        //   .then()
        //   .catch(error => {
        //     this.isError = true;
        //   });
        // this.isError = false;
        this.isSuccess = true;
        //this.initForm();
      },
      initForm() {
        this.username = "";
        this.password = "";
      }
    },
  };
</script>

<style>
body{
  margin:0;
}
form {
  padding: 10px;
}
  .username-input {
    outline : none;
  }
  .username-input.error{
    border : 1px solid red;
  }
  input{
    margin-bottom: 10px;
  }
  button{
    margin-bottom: 20px;
  }
</style>