<script>
import axios from 'axios';

export default {
  data: function () {
    return {
      student: {},
      message: "Welcome to Vue.js!"
    };
  },
  created: function () {
    this.studentShow();
  },
  methods: {
    studentShow: function () {
      console.log(`showing student...`)
      axios.get(`http://localhost:3000/students/${this.$route.params.id}.json`).then(response => {
        console.log(response.data)
        this.student = response.data
      })
    }
  },
};
</script>
  
<template>
  <section id="header" v-if="this.$route.name === 'resumesShow'">
    <header>
      <span class="image avatar"><img src="student.photo" alt="" /></span>
      <h1 id="logo"><a href="#">{{student.first_name}} {{student.last_name}}</a></h1>
      <p>{{student.short_bio}}</p>
    </header>
    <nav id="nav">
      <ul>
        <li><a href="#one" class="active">About Me</a></li>
        <li><a href="#two">Experience</a></li>
        <li><a href="#three">Education</a></li>
        <li><a href="#four">Skills</a></li>
        <li><a href="#five">Capstone</a></li>
        <li><a href="#six">Contact</a></li>
        <li><a href="/resumes">Back to Resumes</a></li>
      </ul>
    </nav>
    <footer>
      <ul class="icons">
        <li><a :href="`http://${student.twitter}`" class="icon brands fa-twitter"><span class="label">Twitter</span></a>
        </li>
        <li><a href="https://www.linkedin.com/in/.../" target="_blank" class="icon brands fa-linkedin"><span
              class="label">LinkedIn</span></a></li>
        <li><a :href="`http://${student.github}`" class="icon brands fa-github"><span class="label">Github</span></a>
        </li>
      </ul>
    </footer>
  </section>

  <div class="home">

    <!-- Wrapper -->
    <div id="wrapper">

      <!-- Main -->
      <div id="main">

        <!-- One -->
        <section id="one">
          <div class="image main" data-position="center">
            <img src="/images/loopsy_daisy.png" alt="" />
          </div>
          <div class="container">
            <header class="major">
              <h2>{{student.first_name}} {{student.last_name}}</h2>
              <p>Software Developer</p>
            </header>
            <p>{{student.short_bio}}</p>
          </div>
        </section>

        <!-- Two -->
        <section id="two">
          <div class="container">
            <h3>Experience</h3>
            <div v-for="experience in student.experience">
              <h4>{{experience.job_title}} - {{experience.company_name}}</h4>
              <div class="row">
                <div class="col-6 col-12-xsmall">
                  <ul class="alt">
                    <li>{{experience.start_date}} - {{experience.end_date}}</li>
                    <h5>details:</h5>
                    <p>{{experience.details}}</p>
                  </ul>
                </div>
              </div>
            </div>
          </div>
        </section>

        <!-- Three -->
        <section id="three">
          <div class="container">
            <h3>Education</h3>
            <div v-for="education in student.education">
              <h4>{{education.university_name}} - {{education.degree}}</h4>
              <div class="row">
                <div class="col-6 col-12-xsmall">
                  <ul class="alt">
                    <li>{{education.start_date}} - {{education.end_date}}</li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
        </section>

        <!-- four -->
        <section id="four">
          <div class="container">
            <h3>Skills</h3>
            <div v-for="skill in student.skills">
              <div class="features">
                <h5>{{skill.skill}}</h5>
              </div>
            </div>
          </div>
        </section>

        <!-- five -->
        <section id="five">
          <div class="container">
            <h3>{{student.capstone.name}}</h3>
            <div class="features">
              <article>
                <a href="#" class="image"><img v-bind:src="student.capstone.screenshot" alt="" /></a>
                <div class="inner">
                  <p>{{student.capstone.description}}</p>
                </div>
                <p></p>
                <a v-bind:href="student.capstone.url" class="text">Demo Url</a>
              </article>
            </div>
          </div>
        </section>

        <!-- six -->
        <section id="six">
          <div class="container">
            <h3>Contact Me</h3>
            <ul class="alt">
              email: {{student.email}} <br />
              phone: {{student.phone_number}} <br />
              <a :href="`${student.website}`">website</a>
            </ul>
          </div>
        </section>
      </div>
    </div>
  </div>
</template>
  
<style>

</style>