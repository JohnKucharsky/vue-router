<template>
  <div v-if="job">
    <h1>
      {{ job.name }}
    </h1>
    <p>The user id is {{ id }}</p>
    <p>
      {{ job.email }}
    </p>
  </div>
  <div v-else>
    <p>Loading job details...</p>
  </div>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      job: null,
    };
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/users/" + this.id)
      .then((res) => res.json())
      .then((data) => (this.job = data))
      .catch((err) => console.log(err.message));
  },
  //   data() {
  //     return {
  //       id: this.$route.params.id,
  //     };
  //   },
};
</script>

<style></style>
