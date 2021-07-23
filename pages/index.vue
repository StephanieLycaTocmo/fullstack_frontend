<template>
  <div>
    <NavBar />
  
    <div class="container">
      <h1 class="mt-3">Welcome</h1>
      <p v-if="$auth.loggedIn">
        User: {{$auth.user.name}} <br> Email: {{$auth.user.email}}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  auth: false
}
</script>

<style>
h1 {
  text-align: center;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}
p {
  padding-top: 50px;
  text-align: center;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  text-emphasis-style: bold;
}
.container {
    padding: 25px;
}
</style>