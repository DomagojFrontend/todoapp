<template>
  <transition name="bounce">
    <div class="transform transition-all duration-150 h-14">
      <div class="flex flex-row gap-5 items-center">
        <div
          :class="`transition-all ease-in-out duration-500 text-lg font-bold ${
            task.done ? 'is-complete' : ''
          }`"
        >
          {{ task.content }}
        </div>
        <div class="flex flex-row gap-5">
          <button
            class="
              bg-green-500
              text-white
              font-bold
              px-4
              py-2
              rounded-xl
              transition-all
              ease-in-out
              duration-150
              border-2 border-transparent
              hover:bg-transparent hover:border-green-500 hover:text-gray-600
            "
            @click="toggleDone"
          >
            {{ task.done ? "Undo" : "Done" }}
          </button>
          <button
            class="
              bg-btnDelete
              text-white
              font-bold
              px-4
              py-2
              rounded-xl
              transition-all
              ease-in-out
              duration-150
              border-2 border-transparent
              hover:bg-transparent hover:border-btnDelete hover:text-gray-600
            "
            @click="removeTask"
          >
            Delete
          </button>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  props: ["task"],
  methods: {
    toggleDone() {
      this.$store.commit("TOGGLE_TASK", this.task);
    },
    removeTask() {
      this.$store.commit("REMOVE_TASK", this.task);
    },
  },
};
</script>
