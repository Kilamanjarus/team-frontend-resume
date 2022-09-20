<template>
  <div id="app">
    <!-- Header -->

    <!-- Router View -->
    <router-view />

    <!-- Footer -->
    <section id="footer">
      <div class="container">
        <ul class="copyright">
          <router-link to="/resumes">Home</router-link> |
          <router-link to="/login">Login</router-link> |
          <router-link to="/signup">Signup</router-link>
          <li>&copy; Untitled. All rights reserved.</li>
          <li>Design: <a href="http://html5up.net">HTML5 UP</a></li>
        </ul>
      </div>
    </section>
  </div>

</template>