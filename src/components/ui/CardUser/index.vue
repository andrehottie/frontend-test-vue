<template>
  <div class="user-card">
    <div class="section">
      <div class="user-name">
        <p>{{ user.firstName }} {{ user.lastName }}</p>
      </div>
      <ProfilePic :src="user.profilePic" />
    </div>
    <div class="section">
      <p>Contacts:</p>
      <a class="user-phone" :href="`tel:${user.phone}`"
        ><img class="btn" :src="phoneSVG"
      /></a>
      <a class="user-email" :href="`mailto:${user.email}`"
        ><img class="btn" :src="mailSVG"
      /></a>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import { TUser } from "@/declarations/User";
import ProfilePic from "../ProfilePic/index.vue";

interface ComponentData {
  phoneSVG: string;
  mailSVG: string;
}

@Component({ components: { ProfilePic } })
export default class CardUser extends Vue {
  @Prop()
  private user!: TUser;
  data(): ComponentData {
    return {
      phoneSVG: require("../../../assets/phone.svg"),
      mailSVG: require("../../../assets/mail.svg"),
    };
  }
}
</script>

<style scoped>
.user-card {
  background-color: #f9f9f9;
  box-shadow: 0px 1px 3px rgb(0 0 0 / 40%);
  -webkit-box-shadow: 0px 1px 3px rgb(0 0 0 / 40%);
  -moz-box-shadow: 0px 1px 3px rgb(0 0 0 / 40%);
  border-radius: 10px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  margin: 20px 0;
  padding: 10px 15px;
}
.section {
  margin: 0 25px;
}
.user-name {
  margin: 5px;
}
.btn {
  width: 40px;
}
a {
  color: #42b983;
}
p {
  margin: 5px;
}
</style>
