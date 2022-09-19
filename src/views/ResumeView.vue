<script>
  import axios from "axios";
  export default {
    data: function () {
      return {
        students:
          first_name: "John",
          last_name: "Doe",
      },
      }
    },
    created: function () {
      this.indexStudent();
    },
    methods: {
      indexStudent: function () {
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
      <div v-for="student in students" >
      <a v-bind:href="/resumes/${students.id}">{{ student.first_name }} {{student.last_name}}</a>
        
      </div>
    </div>
  </template>