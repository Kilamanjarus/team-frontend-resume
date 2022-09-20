<script>
import axios from "axios";
export default {
  data: function () {
    return {
      students: [],
    };
  },
  created: function () {
    this.indexStudents();
  },
  methods: {
    indexStudents: function () {
      axios.get("/students.json").then(response => {
        console.log("students index", response.data);
        this.students = response.data;
      });
    },
  },
};
</script>
  
<template>
  <div class="students-index">
    <h1>All Students</h1>
    <div v-for="student in students">
      <h3>{{ student.first_name }}</h3>
      <!-- <img v-bind:src="student.url" v-bind:alt="student.name" /> -->
    </div>
  </div>
  <!-- Three -->
  <section id="three">
    <div class="container">
      <h3>Students</h3>
      <p>Student Name and a picture of their capstone</p>
      <div class="features">
        <div v-for="student in students">
          <article>
            <!-- <a v-bind:href="`http://localhost:8080/resumes/${student.id}`" class="image"><img v-bind:src="student.photo" alt="" /></a> -->
            <a v-bind:href="`http://localhost:8080/resumes/${student.id}`" class="image"><img
                src="https://i.etsystatic.com/30677692/r/il/71638b/3580232855/il_fullxfull.3580232855_q0k0.jpg"
                alt="" /></a>
            <div class="inner">
              <h4>{{student.first_name}} {{student.last_name}}</h4>
              <p></p>
            </div>
          </article>
        </div>
      </div>
    </div>
  </section>
</template>
