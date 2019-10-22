<template>
  <div id="app">
    <!-- <div id="nav">
      <router-link to="/">Home</router-link>|
      <router-link to="/about">About</router-link>
    </div>-->
    <div id="cover"></div>
    <div id="todo_wrap">
      <Header></Header>
      <ToDo></ToDo>
      <Footer></Footer>
    </div>
    <!-- <router-view /> -->
  </div>
</template>
<script>
import Header from "./todo/header.vue";
import Footer from "./todo/footer.jsx";
import ToDo from "./todo/todo.vue";
export default {
  components: {
    Header,
    Footer,
    ToDo
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  position: absolute;
  top: 0;
  right: 0;
  left: 0;
  height: 100%;
  background: url("./assets/images/bj1.jpg") no-repeat center center;
  background-size: cover;
}
#cover {
  position: absolute;
  top: 0;
  right: 0;
  left: 0;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
}
#todo_wrap {
  /* 中间内容部分 */
  /* width: 800px;
  background: #fff;
  margin: 66px auto;
  padding: 20px;
  position: absolute;
  top: 0;
  right: 0;
  left: 0; */
  position: absolute;
  top: 0;
  right: 0;
  left: 0;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);

  overflow: hidden;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
