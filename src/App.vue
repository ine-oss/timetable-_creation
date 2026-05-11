<script setup>
import { ref } from 'vue';

const lessons = ref([
  { subject: 'JavaScript', time: '09:00', study: 'Vue Directives' },
  { subject: 'Math', time: '10:30', study: 'Functions' },
  { subject: 'Physics', time: '13:00', study: 'Motion' },
  { subject: 'French', time: '14:30', study: 'Vocabulary' },
  { subject: 'English', time: '16:00', study: 'Grammar' }
]);

const activeLesson = ref(null);

const selectLesson = (lesson) => {
  activeLesson.value = lesson;
};
</script>

<template>
  <div>
    <h1>School Timetable</h1>

    <table border="1">
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
          <td>{{ item.subject }}</td>
          <td>
            <button @click="selectLesson(item)">View Study Plan</button>
          </td>
        </tr>
      </tbody>
    </table>

    <div v-if="activeLesson">
      <hr>
      <h2>Study Details: {{ activeLesson.subject }}</h2>
      <p>Today we study: {{ activeLesson.study }}</p>
      <button @click="activeLesson = null">Close</button>
    </div>
  </div>
</template>