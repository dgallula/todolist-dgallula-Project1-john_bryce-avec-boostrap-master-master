<template>
  <div class="todolist-container">
    <h1>Ma Todo List</h1>
    
    <form action="" @submit.prevent="addTodo">
      <fieldset role="group">
        <input v-model="newTodo" placeholder="Nouvelle tâche...">
        <button type="submit">Ajouter</button>
      </fieldset>
    </form>
    
    <div v-if="todos.length === 0">Aucune tâche à faire.</div>
    
    <ul>
      <li v-for="todo in filteredTodos" :key="todo.date" :class="{ completed: todo.completed }">
        <input type="checkbox" v-model="todo.completed">
        {{ todo.title }}
      </li>
    </ul>
    
    <div class="footer">
      <label>
        <input type="checkbox" v-model="hideCompleted">
        Masquer les tâches terminées
      </label>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

// Variables réactives
const newTodo = ref('')

const todos = ref([
  { title: "Acheter la propriété 'Rue de la Paix'", completed: false, date: Date.now() + 1 },
  { title: "Construire un hôtel sur 'Avenue Foch'", completed: false, date: Date.now() + 2 },
  { title: "Éviter la case prison", completed: false, date: Date.now() + 3 }
])

const hideCompleted = ref(false)

// Fonction pour ajouter une nouvelle tâche
const addTodo = () => {
  if (newTodo.value.trim()) {
    todos.value.push({
      title: newTodo.value,
      completed: false,
      date: Date.now()
    })
    newTodo.value = ''
  }
}

// Computed property pour filtrer les tâches
const filteredTodos = computed(() => {
  return hideCompleted.value
    ? todos.value.filter(todo => !todo.completed)
    : todos.value
})
</script>

<style>
.todolist-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

h1 {
  font-size: 24px;
  margin-bottom: 20px;
  color: #333;
  text-align: center;
}

fieldset {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

input[type="text"] {
  flex-grow: 1;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button[type="submit"] {
  padding: 10px 20px;
  font-size: 16px;
  color: #fff;
  background-color: #007bff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button[type="submit"]:hover {
  background-color: #0056b3;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  display: flex;
  align-items: center;
  padding: 10px;
  border-bottom: 1px solid #ddd;
}

button[type="submit"] {
  padding: 10px 20px;
  font-size: 16px;
  color: #fff;
  background-color: #8ea728; /* Couleur de fond verte */
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button[type="submit"]:hover {
  background-color: #218838; /* Couleur verte plus foncée lors du survol */
}

li:last-child {
  border-bottom: none;
}

li.completed {
  text-decoration: line-through;
  color: #888;
}

.footer {
  margin-top: 20px;
  text-align: center;
}

label {
  font-size: 16px;
}
</style>

