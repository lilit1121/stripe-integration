<template>
  <div>
    <sidebar />
    <Menu />
    <router-view/>
  </div>
</template>

<script>
  import Sidebar from './components/Sidebar.vue'
  import Menu from './components/Menu.vue'

  export default {
    components: {
      Sidebar,
      Menu
    }
  }
</script>

<style>
  input[type="text"], input[type="date"]{
    border: 2px solid #17a2b8;
    border-radius: 0.25rem !important;
    padding: 10px;
    outline: none;
  }
  input[type="radio"]{
    position: relative;
    outline: none;
    width: 16px;
    height: 16px;
    cursor: pointer;
  }
  input[type="radio"]:checked::before{
    content: '';
    background-color: white;
    border: 4px solid #17a2b8;
    width: 18px;
    height: 18px;
    position: absolute;
    top: -1px;
    border-radius: 50%;
    cursor: pointer;
    left: -0.5px;
  }
  .cursor-pointer{
    cursor: pointer;
  }
  .error{
    padding: 5px;
    font-size: 14px;
    margin-bottom: 0;
  }
  .blue-btn{
    padding: 10px 0;
  }
  .page{
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 500px;
  }

  @media only screen and (max-width: 600px) {
    .page{
      width: 300px;
    }
  }
</style>
