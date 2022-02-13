<template>
    <div id="shopping-form">
    <form @submit.prevent='handleSubmit'>
      <label>Excercise</label>
      <input v-model="item.name" type="text" />
      <label>Number of Sets</label>
      <input v-model="item.sets" type="number" />
      <label>Number of Reps</label>
      <input v-model="item.reps" type="number" />
      <label>Total Weight, 0 if not applicable</label>
      <input v-model="item.weights" type="number" />
      <button>Add item</button>
    </form>
  </div>
</template>

<script>
export default {
    name: 'shopping-form',
    data() {
      return {
        item: {
          name: '',
          sets: '',
          reps: '',
          weights: '',
        },
      }
    },
    methods: {
        handleSubmit() {
            this.$emit('add:item', this.item)
            this.item = {
                name: '',
                sets: '',
                reps: '',
                weights: '',
            }
        }
    }
}
</script>

<style>
form {
    margin-bottom: 2rem;
  }
</style>