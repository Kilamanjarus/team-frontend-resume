<script>
  import axios from "axios";
  export default {
    data: function () {
      return {
        resumes: [],
      };
    },
    created: function () {
      this.showResume();
    },
    methods: {
      showResume: function () {
        axios.get("/resumes").then((response) => {
          console.log("resumes index", response);
          this.resumes = response.data;
        });
      },
    },
  };
  </script>
  
  <template>
    <div class="resumes-index">
      <h1>All resumes</h1>
      <div v-for="photo in resumes" v-bind:key="photo.id">
        <h2>{{ photo.name }}</h2>
        <img v-bind:src="photo.url" v-bind:alt="photo.name" />
        <p>Width: {{ photo.width }}</p>
        <p>Height: {{ photo.height }}</p>
      </div>
    </div>
  </template>
