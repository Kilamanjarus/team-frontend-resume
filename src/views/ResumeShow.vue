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
      <span class="image avatar"><img src="/images/avatar.jpg" alt="" /></span>
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
            <img src="/images/banner.jpg" alt="" />
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
            <h3>A Few Accomplishments</h3>
            <p>Integer eu ante ornare amet commetus vestibulum blandit integer in curae ac faucibus integer non.
              Adipiscing cubilia elementum integer. Integer eu ante ornare amet commetus.</p>
            <div class="features">
              <article>
                <a href="#" class="image"><img src="/images/pic01.jpg" alt="" /></a>
                <div class="inner">
                  <h4>Possibly broke spacetime</h4>
                  <p>Integer eu ante ornare amet commetus vestibulum blandit integer in curae ac faucibus integer
                    adipiscing ornare amet.</p>
                </div>
              </article>
              <article>
                <a href="#" class="image"><img src="/images/pic02.jpg" alt="" /></a>
                <div class="inner">
                  <h4>Terraformed a small moon</h4>
                  <p>Integer eu ante ornare amet commetus vestibulum blandit integer in curae ac faucibus integer
                    adipiscing ornare amet.</p>
                </div>
              </article>
              <article>
                <a href="#" class="image"><img src="/images/pic03.jpg" alt="" /></a>
                <div class="inner">
                  <h4>Snapped dark matter in the wild</h4>
                  <p>Integer eu ante ornare amet commetus vestibulum blandit integer in curae ac faucibus integer
                    adipiscing ornare amet.</p>
                </div>
              </article>
            </div>
          </div>
        </section>

        <!-- four -->
        <section id="four">
          <div class="container">
            <h3>A Few Accomplishments</h3>
            <p>Integer eu ante ornare amet commetus vestibulum blandit integer in curae ac faucibus integer non.
              Adipiscing cubilia elementum integer. Integer eu ante ornare amet commetus.</p>
            <div class="features">
              <article>
                <a href="#" class="image"><img src="/images/pic01.jpg" alt="" /></a>
                <div class="inner">
                  <h4>Possibly broke spacetime</h4>
                  <p>Integer eu ante ornare amet commetus vestibulum blandit integer in curae ac faucibus integer
                    adipiscing ornare amet.</p>
                </div>
              </article>
              <article>
                <a href="#" class="image"><img src="/images/pic02.jpg" alt="" /></a>
                <div class="inner">
                  <h4>Terraformed a small moon</h4>
                  <p>Integer eu ante ornare amet commetus vestibulum blandit integer in curae ac faucibus integer
                    adipiscing ornare amet.</p>
                </div>
              </article>
              <article>
                <a href="#" class="image"><img src="/images/pic03.jpg" alt="" /></a>
                <div class="inner">
                  <h4>Snapped dark matter in the wild</h4>
                  <p>Integer eu ante ornare amet commetus vestibulum blandit integer in curae ac faucibus integer
                    adipiscing ornare amet.</p>
                </div>
              </article>
            </div>
          </div>
        </section>

        <!-- five -->
        <section id="five">
          <div class="container">
            <h3>Capstone</h3>
            <p>Capstone.description will go here</p>
            <div class="features">
              <article>
                <a href="#" class="image"><img src="/images/pic01.jpg" alt="" /></a>
                <div class="inner">
                  <h4>Capstone Screenshot</h4>
                  <p>This is the screenshop demonstration of the capstone project</p>
                </div>
                <p></p>
                <a href="#" class="text">Demo Url</a>
              </article>
            </div>
          </div>
        </section>

        <!-- six -->
        <section id="six">
          <div class="container">
            <h3>Contact Me</h3>
            <p>Integer eu ante ornare amet commetus vestibulum blandit integer in curae ac faucibus integer non.
              Adipiscing cubilia elementum integer. Integer eu ante ornare amet commetus.</p>
            <form method="post" action="#">
              <div class="row gtr-uniform">
                <div class="col-6 col-12-xsmall"><input type="text" name="name" id="name" placeholder="Name" /></div>
                <div class="col-6 col-12-xsmall"><input type="email" name="email" id="email" placeholder="Email" />
                </div>
                <div class="col-12"><input type="text" name="subject" id="subject" placeholder="Subject" /></div>
                <div class="col-12"><textarea name="message" id="message" placeholder="Message" rows="6"></textarea>
                </div>
                <div class="col-12">
                  <ul class="actions">
                    <li><input type="submit" class="primary" value="Send Message" /></li>
                    <li><input type="reset" value="Reset Form" /></li>
                  </ul>
                </div>
              </div>
            </form>
          </div>
        </section>
      </div>
    </div>
  </div>
</template>
  
<style>

</style>