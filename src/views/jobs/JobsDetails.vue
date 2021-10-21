<template>
  <div v-if="job">
    <h3>{{ job.title }}</h3>
    <p>This is the details {{ job.details }}</p>
    <p>Id is: {{ job.id }}</p>
  </div>
  <div v-else>
    No data yet
  </div>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      // id: this.$route.params.id,
      job: null,
    };
  },
  mounted() {
    fetch("http://localhost:3000/jobs/" + this.id)
      .then((res) => res.json())
      .then((data) => (this.job = data))
      .catch((err) => console.log(err.message));
  },
};
</script>

<style></style>
