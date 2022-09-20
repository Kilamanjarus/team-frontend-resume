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
          console.log("students index", response);
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
        <h2>{{ student.first_name }}</h2>
        <!-- <img v-bind:src="student.url" v-bind:alt="student.name" /> -->
      </div>
    </div>
  </template>
