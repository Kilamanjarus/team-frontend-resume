
<script>
  import axios from "axios";
  export default {
    data: function () {
      return {
        students:[{
          first_name: "John",
          last_name: "Doe"
        }]
      };
    },
    created: function () {
      // this.indexStudents();
    },
    methods: {
      indexStudents: function () {
        axios.get("/students").then((response) => {
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

        <!-- <h2>{{ students.first_name }}</h2> -->

        <!-- <a v-bind:href="/resumes/${student.id}">{{ student.first_name }} {{student.last_name}}</a> -->
        {{student}}
      
      </div>
    </div>
  </template>

  <style></style>

