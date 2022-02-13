<template>
<h1>Trents Excercise Tracker</h1>
  <ShoppingListForm @add:item='addItem' />
  <ShoppingList 
  @delete:item='deleteItem'
  @edit:item='editItem'
  :items='shoppingItems' />
</template>

<script>
import ShoppingList from './components/ShoppingList.vue'
import ShoppingListForm from './components/ShoppingListForm.vue'
export default {
  name: 'App',
  components: {
    ShoppingList,
    ShoppingListForm
  },
  data() {
    return {
      hideCompleted: false, 
      shoppingItems: [
        {
          id: 1,
          name: 'Push-ups',
          sets: 3,
          reps: 5,
          weights: 0,
          done: true, 
        },
        {
          id: 2,
          name: 'Sit-ups',
          sets: 2,
          reps: 10,
          weights: 0,
        },
        {
          id: 3,
          name: 'Squats',
          sets: 3,
          reps: 12,
          weights: 0,
        },
        {
          id: 4,
          name: 'Bicep Curls',
          sets: 3,
          reps: 10,
          weights: 10,
        },
      ]
    }
  },
  computed: {
    filteredTodos() {
      return this.hideCompleted
        ? this.todos.filter((t) => !t.done)
        : this.todos
    }
  },
  methods: {
    addItem(item) {
      //make an id too
      const lastId = this.shoppingItems.length > 0
      ? this.shoppingItems[this.shoppingItems.length -1].id
      : 0;
      const id = lastId + 1;
      const newItem = { ...item, id}
      this.shoppingItems = [ ...this.shoppingItems, newItem]
    },
    deleteItem(id) {
      this.shoppingItems = this.shoppingItems.filter(item => item.id !== id)
    },
    editItem(id, updatedItem) {
      this.shoppingItems = this.shoppingItems
        .map(item => {
          return item.id === id ? updatedItem : item
        })
    }
  }
}
</script>

<style>
.done {
  text-decoration: line-through;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
