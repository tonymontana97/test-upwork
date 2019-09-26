<template>
  <div class="register">
    <div class="form-group">
      <label>
        <input type="email" required v-model="email" placeholder="E-mail" class="form-control">
      </label>
    </div>
    <div class="form-group">
      <label>
        <input type="password" required v-model="password" placeholder="Password" class="form-control">
      </label>
    </div>
    <button type="submit" @click="submitForm">Sign In</button>

  </div>
</template>

<script lang="ts">
  import {Vue} from 'vue-property-decorator';
  import firebase from 'firebase';
  import router from '@/router';

  export default Vue.extend({
    data() {
      return {
        email: '',
        password: ''
      }
    },
    methods: {
      submitForm() {
        firebase.auth().signInWithEmailAndPassword(this.email, this.password).then((user) => {
          router.push({
            name: 'dashboard'
          })
        }).catch((err) => {
          console.log(err);
        })

      }
    }
  });
</script>
