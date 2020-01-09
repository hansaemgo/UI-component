<template>
  <div>
    <form v-on:submit.prevent="submitForm"> 
      <div>
        <label for="username">ID : </label>
        <input id="username" type="text" v-model="username">
      </div>
       <div>
        <label for="password">PW : </label>
        <input id="password" type="password" v-model="password">
      </div>
      <button type="submit">로그인</button>
    </form>
    <p v-if="isError">올바르지 않은 ID입니다.</p>
  </div>
</template>

<script>
export default {
    data() {
      return {
        username: '',
        password: '',
        isError: false,
      };
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
        this.isError = true;
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

</style>