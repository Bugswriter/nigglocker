<template>
<div id="add-login">
  <h2 class="m-3">Create New Login</h2>
  <hr>
  <b-col cols="8">
    <b-form v-if="!submitted">
      <b-form-group  id="input-group-1" label="🌐 Website address" label-for="input-1">
        <b-form-input v-model="login.website" id="input-1" type="text" placeholder="example: www.foobar.com/login" required></b-form-input>
      </b-form-group>
      <b-form-group  id="input-group-2" label="👤 Username" label-for="input-2">
        <b-form-input v-model="login.username" id="input-2" type="text"></b-form-input>
      </b-form-group>
      <b-form-group id="input-group-3" label="🔑 Password" label-for="input-3">
        <b-form-input v-model="login.password" id="input-3" type="password"></b-form-input>
      </b-form-group>
      <b-button v-on:click.prevent="post" variant="primary">Save</b-button>
      <b-button class="ml-3">Cancel</b-button>
    </b-form>
    <h3 v-if="submitted">Thanks for submitting your login!</h3>
  </b-col>
</div>
</template>

<script type="text/javascript">
  export default {
      data(){
          return {
              login: {
                  website: '',
                  username: '',
                  password: ''
              },
              submitted: false
          }
      },
      methods: {
          post: function(){
              this.$http.post('https://nigglocker.firebaseio.com/logins.json', this.login).then(function(data){
                  console.log(data);
                  this.submitted = true;
              });
          }
      }
  }
</script>

<style  scoped>

</style>
