<template>
  <div>
      <nav class="navbar navbar-light bg-light sticky-top">
        <div class="container">
          <a class="navbar-brand" href="#">Newlix</a>
          <!-- <input type="checkbox" class='theme-switch'/> -->
          <div class="custom-control custom-checkbox">
            <input type="checkbox" class="custom-control-input" id="checkDarkMode" v-model="darkMode">
            <label class="custom-control-label" for="checkDarkMode">Dark Mode</label>
          </div>
        </div>
      </nav>
      <nuxt />
      <footer class="footer bg-primary py-3">
        <div class="container">
          <div class="row">
            <div class="col-md-12 text-center">
              <h6 class="subtitle-2">Powered by NewsApi.org</h6>
            </div>
        </div>
        </div>
      </footer>
  </div>
</template>

<style lang="scss">
  @import "../assets/sass/main.scss";
</style>
 
 <script>
  export default {
        name: 'app',
        data() {
            return {
                darkMode: false,
            }
        },
        mounted() {

            // check for active theme
            let htmlElement = document.documentElement;
            let theme = localStorage.getItem("theme");

            if (theme === 'dark') {
                htmlElement.setAttribute('theme', 'dark')
                this.darkMode = true
            } else {
                htmlElement.setAttribute('theme', 'light');
                this.darkMode = false
            }
        },
        watch: {
            darkMode: function () {
                // add/remove class to/from html tag
                let htmlElement = document.documentElement;

                if (this.darkMode) {
                    localStorage.setItem("theme", 'dark');
                    htmlElement.setAttribute('theme', 'dark');
                } else {
                    localStorage.setItem("theme", 'light');
                    htmlElement.setAttribute('theme', 'light');
                }
            }
        }
    }
 </script>