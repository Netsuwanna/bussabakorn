
<template>
<v-parallax src="/pic/36363298_2190747631154448_5291861013929394176_n.jpg"">
  <div>
    <br>
      <router-link :to="{ path: '/student'}" replace><center>
      <div class="text-xs-center">
        <v-btn round color="pink" dark>Welcome</v-btn>
      </div>
    </center>
    </router-link>
  </div>

</v-parallax>

</template>

<script>
export default {
  layout : "default",
  data() {
    return {
      id: 1,
    }
  },
  styleObject: {
    font: '.font-weight-regular.font-italic',
  },
}
</script>
