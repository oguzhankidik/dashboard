<template>
  <div class="main">
    <Charts v-bind:message="posts.online_guests" />
    <Infos v-bind:message2="this.posts"/>
    <div class="bottominfos">
      <PieChart v-bind:message3="posts.device_vendors" />
      <PieChart v-bind:message3="posts.login_types" />
    </div>
  </div>
</template>

<script>
import Infos from "@/components/Infos";
import Charts from "@/components/Charts";
import axios from "axios";

import PieChart from "@/components/PieChart";


export default {
  components: {
    PieChart, Charts,Infos,
  },

  name: 'Dashboard',
  props: {
    msg: String
  },
  created() {
    this.getPosts();
  },
  data() {
    return {
      posts: [],
      errors: []
    };
  },
  methods: {
    async getPosts() {

      const response=await axios
          .get("http://challenge.iperasolutions.com/dashboard");
      this.posts=response.data

      axios
          .get("http://challenge.iperasolutions.com/dashboard")
          .then(response => (this.posts = response.data))
          .catch(error => {
            this.errors.push(error);
          });
    }
  }
}
</script>


<style scoped>
.bottominfos{
  display: flex;
  padding: 20px;
  justify-content: space-between;
}

</style>
