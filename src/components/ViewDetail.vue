<template>
  <div>
    <h3>Todo Detail</h3>
    <p class="title">{{ especificTodo.title }}</p>
    <p
      :class="[
        especificTodo.completed == false ? 'isNotCompleted' : 'isCompleted',
      ]"
    >
      {{ especificTodo.completed }}
    </p>
  </div>
</template>
<script>
import { mapGetters, mapActions } from "vuex";
export default {
  name: "ViewDetail",
  methods: {
    ...mapActions(["getDetail"]),
  },
  computed: {
    ...mapGetters(["especificTodo"]),
  },
  created() {
    this.getDetail(this.$route.params.id);
  },
};
</script>

<style>
h3 {
  color: #41b883;
  text-align: center;
  letter-spacing: 5px;
  font-size: 40px;
}
.isCompleted {
  color: #41b883;
}

.isNotCompleted {
  color: #d13c3c;
  text-decoration: line-through;
}
</style>