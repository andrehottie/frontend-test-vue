<template>
  <div class="users-list">
    <ul>
      <li v-for="user in users" :key="user.id">
        <CardUser :user="user" />
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { TUser } from "@/declarations/User";
import CardUser from "@/components/ui/CardUser/index.vue";
import { Component, Vue } from "vue-property-decorator";

declare interface ComponentData {
  users: TUser[];
}

@Component({
  components: {
    CardUser,
  },
})
export default class UserList extends Vue {
  users!: TUser[]; // se non dichiaro users quì, il this.users a riga 36 mi da errore

  data(): ComponentData {
    return {
      users: [],
    };
  }
  beforeCreate(): void {
    fetch("users")
      .then((res) => res.json())
      .then((data) => {
        this.users = data;
      });
  }
}
</script>

<style scoped>
p {
  color: blue;
}
ul {
  list-style: none;
  padding: 0;
}
.users-list {
  display: flex;
  justify-content: center;
}
</style>
