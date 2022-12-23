<template>
  <router-link :to="{name:'AllCategory'}">
    <button class="btn btn-primary btn-log">admin category</button>

  </router-link>
  <router-link :to="{name:'AllProduct'}">
    <button class="btn btn-primary btn-log">admin products</button>

  </router-link>
</template>
<script>
export default{
  name:"AdminView",
}
</script>
