<script setup>
import { ref } from 'vue';

const lessons = ref([
  { subject: 'JavaScript', code: 'JS', time: '09:00', study: 'Vue Directives' },
  { subject: 'Math', code: 'MTC', time: '10:30', study: 'Functions' },
  { subject: 'Physics', code: 'PHY', time: '13:00', study: 'Motion' },
  { subject: 'User Interface', code: 'UI', time: '14:30', study: 'Design Systems' },
  { subject: 'Interaction', code: 'IX', time: '16:00', study: 'User Flows' }
]);

const activeLesson = ref(null);

const selectLesson = (lesson) => {
  activeLesson.value = lesson;
};
</script>

<template>
  <div class="container">
    <h1>Timetable</h1>

    <table>
      <thead>
        <tr>
          <th>Time</th>
          <th>Subject</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in lessons" :key="item.subject">
          <td>{{ item.time }}</td>
          <td><strong>{{ item.code }}</strong> - {{ item.subject }}</td>
          <td>
            <button @click="selectLesson(item)">View</button>
          </td>
        </tr>
      </tbody>
    </table>

    <div v-if="activeLesson" class="info-box">
      <h3>{{ activeLesson.subject }} Details</h3>
      <p>Focus: {{ activeLesson.study }}</p>
      <button class="secondary" @click="activeLesson = null">Close</button>
    </div>
  </div>
</template>

<style scoped>
/* Simple CSS Reset & Layout */
.container {
  max-width: 500px;
  margin: 2rem auto;
  font-family: sans-serif;
  color: #333;
}

h1 {
  border-bottom: 2px solid #eee;
  padding-bottom: 10px;
}

/* Table Styling */
table {
  width: 100%;
  border-collapse: collapse;
  margin-bottom: 20px;
}

th {
  text-align: left;
  background: #f4f4f4;
  padding: 10px;
}

td {
  padding: 10px;
  border-bottom: 1px solid #eee;
}

/* Buttons */
button {
  cursor: pointer;
  background: #007bff;
  color: white;
  border: none;
  padding: 5px 12px;
  border-radius: 4px;
}

button:hover {
  background: #0056b3;
}

button.secondary {
  background: #6c757d;
}

/* Information Box */
.info-box {
  background: #e9ecef;
  padding: 15px;
  border-radius: 8px;
  border-left: 4px solid #007bff;
}
</style>