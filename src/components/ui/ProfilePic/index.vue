<template>
  <img class="profile-pic" :src="`${!!src ? src : userSVG}`" />
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

interface ComponentData {
  src?: string;
  userSVG: string;
}

@Component
export default class ProfilePic extends Vue {
  @Prop()
  private src!: string;
  data(): ComponentData {
    return {
      userSVG: require("../../../assets/user.svg"),
    };
  }
}
</script>

<style scoped>
.profile-pic {
  width: 40px;
  object-fit: cover;
  border-radius: 50%;
  height: 40px;
}
</style>
