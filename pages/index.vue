<template>
  <main class="text-gray-600 w-full h-screen items-center flex justify-center">
    <div
      class="
        flex flex-col
        h-auto
        gap-8
        items-center
        z-10
        py-5
        px-5
        shadow-2xl
        bg-cover
      "
      :style="{
        'background-image': `url(${require('@/assets/img/background.png')})`,
      }"
    >
      <div class="flex flex-col text-center">
        <h1 class="text-4xl font-bold">Task Board</h1>
        <p class="text-xl font-medium">Create a list of tasks</p>
      </div>
      <div class="flex flex-row gap-5">
        <input
          class="
            bg-transparent
            text-gray-500 text-lg
            py-3
            px-6
            focus:outline-none
          "
          type="text"
          v-model="newTask"
          placeholder="Add a new task"
          @keypress.enter="addTask"
        />
        <button class="" @click="addTask">
          <svg class="h-10 w-10" viewBox="0 0 20 20" fill="currentColor">
            <path
              d="M13.586 3.586a2 2 0 112.828 2.828l-.793.793-2.828-2.828.793-.793zM11.379 5.793L3 14.172V17h2.828l8.38-8.379-2.83-2.828z"
            />
          </svg>
        </button>
      </div>

      <div class="flex flex-col gap-2">
        <Task v-for="(task, i) in $store.state.tasks" :key="i" :task="task" />
      </div>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      newTask: "",
    };
  },
  methods: {
    addTask() {
      if (this.newTask) {
        this.$store.commit("ADD_TASK", this.newTask);
        this.newTask = "";
      }
    },
  },
};
</script>
