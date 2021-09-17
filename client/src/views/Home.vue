<template>
  <div class="home">
    Welcome to the website click fetch users to fetch the list of all users.
    <button class="ml-4 btn btn-light" @click="getAllUsersFromDB">fetch users</button>
    <div class="row">
      <div v-for="(user,index) of userArray" :key="index" class="col-md-3 col-sm-6 col-xs-12">
        <div class="card bg-default text-white">
          <div class="card-body">
            <h5 class="card-title text-success">User: {{ user.name }}</h5>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions } from "vuex";
export default {
  name: "home",
  components: {},
  data() {
    return {
      userArray: []
    }
  },
  methods: {
    ...mapActions(["getAllUsers"]),
    async getAllUsersFromDB() {
      this.userArray = await this.getAllUsers()
    }
  }
};
</script>