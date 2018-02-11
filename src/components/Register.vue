<template>
  <div>
      <div class="container">
          <div class="row">
              <div class="col s12 m8 offset-m2">
                  <div class="login card-panel grey lighten-4 black-text center">
                      <h3>Register</h3>
                      <form>
                          <div class="input-field">
                              <i class="material-icons prefix">email</i>
                              <input v-model="email" type="text" name="email" id="email">
                              <label for="email">Email</label>
                          </div>
                            <div class="input-field">
                              <i class="material-icons prefix">lock</i>
                              <input v-model="password" type="password" name="password" id="password">
                              <label for="password">Password</label>
                          </div>
                          <button v-on:click="register" class="btn btn-large grey lighten-4 black-text">Register</button>
                      </form>
                  </div>
              </div>
          </div>
      </div>
  </div>
</template>
<script>
import firebase from 'firebase'

export default {
  name: 'register',
  data () {
      return {
          email: '',
          password: ''
      };
  },
  methods: {
      register (e) {
          firebase.auth().createUserWithEmailAndPassword(this.email, this.password).then(user => {
              alert(`Account created for ${user.email}`);
                this.$router.go({
                    path: this.$router.path
                });
          }, error => {
              alert(error.message);
          });

          e.preventDefault();
      }
  }
}
</script>

