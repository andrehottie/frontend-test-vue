<template>
  <div class="users">
    <UserList />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import UserList from "@/components/layout/UserList/index.vue"; // @ is an alias to /src

@Component({
  components: {
    UserList,
  },
})
export default class Users extends Vue {}
</script>
