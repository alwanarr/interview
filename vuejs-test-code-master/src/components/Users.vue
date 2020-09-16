<template>
  <div class="main">
    <div class="main-title">
      <h1>{{ msg }}</h1>
    </div>
    <div class="user-count">
      <div class="count">{{ count }}</div>Users
    </div>
    <div class="wrapper">
      <div class="row" v-for="user in users" :key="user.name">
        <div class="card">
          <div class="body-card">
            <div class="title">Name</div>
            <div class="name">
              <b>{{ user.name }}</b>
            </div>
            <div class="wrapper-card">
              <div class="wrapper-card-body">
                <div class="title">Email</div>
                <div class="email">
                  <b>{{ user.email }}</b>
                </div>
              </div>
              <div class="wrapper-card-body">
                <div class="title">Phone</div>
                <div class="phone">
                  <b>{{ user.phone }}</b>
                </div>
              </div>
              <div class="wrapper-card-body">
                <div class="title">Website</div>
                <div class="website">
                  <b>{{ user.website }}</b>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
// import { mapState } from "vuex";
// import { INCREMENT } from "../mutation-types";

export default {
  name: "Users",
  props: {
    msg: String,
  },
  computed: {
    users() {
      return this.$store.getters.getData;
    },
    count() {
      return this.$store.getters.getCountData.length;
    },
  },
  mounted() {
    axios
      .get("https://jsonplaceholder.typicode.com/users")
      .then((response) => {
        this.setData(response.data);
      })
      .catch((error) => {
        this.loading = false;
        console.error(error);
      });
  },
  methods: {
    setData(data) {
      this.$store.dispatch("setData", data);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  display: block;
  margin-block-start: 0;
  margin-block-end: 0;
  margin-inline-start: 0px;
  margin-inline-end: 0px;
  font-weight: 600;
}
.title {
  color: #e1e1e7;
}
.main {
  background-color: #f5f7fa;
  padding: 10px;
}
.count {
  color: #83dd8b;
  font-weight: 800;
  margin-right: 10px;
}
.wrapper {
  display: flex;
  flex-wrap: wrap;
}
.row {
  flex-basis: 50%;
}
.card {
  background-color: #fff;
  display: flex;
  padding: 15px 20px;
  margin: 15px;

  border-radius: 6px;
}
.body-card {
  padding: 15px 15px;
  display: flex;
  flex-direction: column;
  width: 100%;
}

.body-card > .name {
  margin-top: 8px;
}

.wrapper-card {
  margin-top: 18px;

  display: flex;
  justify-content: space-between;
}

.wrapper-card-body > div:nth-child(2) {
  margin-top: 8px;
}

.wrapper-card-body > .website {
  color: #83dd8b;
}
.user-count {
  border-bottom: 1px solid #e1e1e7;
  color: #646464;
  display: flex;
  align-items: center;
}
</style>
