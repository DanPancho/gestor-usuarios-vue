<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <form @submit.prevent="login">
      <div>
        <label>Username:</label>
        <input type="text" id="username" v-model="username" required />
      </div>
      <div>
        <label>Pasword:</label>
        <input type="password" id="password" v-model="password" required />
      </div>
      <button type="submit">Login</button>
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "LoginComponent",
  props: {
    msg: String,
  },
  data() {
    return {
      username: "",
      password: "",
    };
  },
  methods: {
    async login() {
      try {
        const response = await axios.post("http://127.0.0.1:5000/login", {
          username: this.username,
          password: this.password
        });
        if(response.status == 200) { 
          const responseUsr = await axios.get("http://127.0.0.1:5000/users",
          {
            headers: { 
              'Content-Type':'application/json',
              'x-acces-token':response.data.token
            }
          })
          console.log(response);
          console.log(responseUsr);
        }else {
          alert("NO SE PUDO OBTENR EL TOKEN")
        }

      } catch (err) {
        console.log(err);
        alert("ERROR Consula API");
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
