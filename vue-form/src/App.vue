<template>
  <div>
    <ProgressBar></ProgressBar>
    <form v-on:submit.prevent="submitForm">
      <div>
        <label for="username">ID:</label>
        <input
          id="username"
          type="text"
          v-model="username"
          class="username-input"
          v-bind:class="{'error':isError}"
        />
      </div>
      <div>
        <label for="password">PW:</label>
        <input id="password" type="password" v-model="password" />
      </div>
      <button type="submit" v-bind:disabled="!isUsernameValid">로그인</button>
    </form>
    <p v-if="isSuccess">로그인이 되었습니다.</p>
    <!-- <p v-if="isError">올바르지 않은 아이디입니다.</p>
    <p v-if="isUsernameValid">이메일 형식이 맞습니다.</p>-->
    <toast-popup v-bind:open="isSuccess" v-on:close="isSuccess=false"></toast-popup>
    <!-- <ToastPopup></ToastPopup> -->
  </div>
</template>

<script>
import ProgressBar from "@/components/ProgressBar.vue";
import ToastPopup from "@/components/ToastPopup.vue";

function validateEmail(email) {
  //from https://stackoverflow.com/questions/46155/how-to-validate-an-email-address-in-javascript
  const re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
  return re.test(String(email).toLowerCase());
}

export default {
  components: {
    ToastPopup,
    ProgressBar,
  },
  data() {
    return {
      //React의 State
      username: "",
      password: "",
      isError: false,
      isSuccess: false,
    };
  },
  computed: {
    isUsernameValid() {
      return validateEmail(this.username);
    },
  },
  methods: {
    //ES6+ 객체를 생성할 때 향상된 문법
    submitForm(event) {
      event.preventDefault();
      // console.log("submitted");
      console.log("로그인");
      this.isSuccess = true;
      //무조건 에러 발생시키기
      // this.isError = true;
      // this.initForm();
    },
    initForm() {
      this.username = "";
      this.password = "";
    },
  },
};
</script>

<style >
body {
  margin: 0;
}
form {
  padding: 10px 5px;
}
.username-input {
  outline: none;
}
.username-input.error {
  border: 1px solid red;
}
</style>