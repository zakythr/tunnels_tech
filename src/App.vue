<template>
  <div id="app">
    <b-navbar toggleable="lg" type="dark" class="nav-back">
      <b-navbar-brand href="#">Tunnels Technology</b-navbar-brand>
      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item href="#">Home</b-nav-item>
          <b-nav-item href="#" disabled>About</b-nav-item>
          <b-nav-item href="#" disabled>Services</b-nav-item>
          <b-nav-item href="#" disabled>Portofolio</b-nav-item>
          <b-nav-item href="#" disabled>Career</b-nav-item>
          <b-nav-item href="#" disabled>Contact</b-nav-item>
        </b-navbar-nav>

        <b-navbar-nav class="ml-auto">
          <b-nav-form>
            <b-form-input size="sm" class="mr-sm-2" placeholder="Search"></b-form-input>
            <b-button size="sm" class="my-2 my-sm-0" type="submit">
              Search
            </b-button>
          </b-nav-form>

          <b-nav-item-dropdown right>
            <template v-slot:button-content>
              <em>User</em>
            </template>
            <b-dropdown-item href="#">Profile</b-dropdown-item>
            <b-dropdown-item href="#">Sign Out</b-dropdown-item>
          </b-nav-item-dropdown>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>

    <b-container>
      <b-carousel
        class="mb-3"
        id="carousel-1"
        v-model="slide"
        :interval="4000"
        controls
        indicators
        background="#ababab"
        img-width="1024"
        img-height="240"
        style="text-shadow: 1px 1px 2px #333;"
        @sliding-start="onSlideStart"
        @sliding-end="onSlideEnd"
      >
      <!-- Text slides with image -->
        <b-carousel-slide
          align-h="center"
          class="text-center"
          img-src="https://images.unsplash.com/photo-1509225770129-fbcf8a696c0b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1000&q=80"
        >
          <h2>Mobile & Web Development Company</h2>
          <b-button variant="primary">
            Go somewhere
          </b-button>
        </b-carousel-slide>

        <!-- Slides with custom text -->
        <b-carousel-slide
          img-src="https://cdn3.eyeem.com/thumb/42d5c3a1d3f5e16a2b4929462f8223d2eb170617-1482195181608/w/1280"
          align-h="center"
          class="text-center"
        >
          <h2>Mobile & Web Development Company</h2>
          <b-button variant="primary">
            Go somewhere
          </b-button>
        </b-carousel-slide>

        <!-- Slides with image only -->
        <b-carousel-slide
          img-src="https://philipschwarzphotography.files.wordpress.com/2017/08/badlands-national-park-17-7-04826-panorama.jpg"
          align-h="center"
          class="text-center"
        >
          <h2>Mobile & Web Development Company</h2>
          <b-button variant="primary">
            Go somewhere
          </b-button>
        </b-carousel-slide>

        <!-- Slide with blank fluid image to maintain slide aspect ratio -->
        <b-carousel-slide align-h="center" class="text-center" img-src="https://tau0.files.wordpress.com/2014/07/montana_open_range_and_hills_2.jpg">
          <h2>Mobile & Web Development Company</h2>
          <b-button variant="primary">
            Go somewhere
          </b-button>
        </b-carousel-slide>
      </b-carousel>

      <hr>

    <b-card-group>
      <b-card title="ANDROID APPS DEVELOPMENT"
            img-src="data:image/jpeg;base64,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"
            img-alt="Image"
            img-top
            class="mb-3"
      >
        <b-card-text>
          We Develop Native Android Apps with high performance & best user experience. You will get your best Apps.
        </b-card-text>
        <template v-slot:footer>
          <small class="text-muted">
            <b-button size="sm" variant="info" @click="handleClick">
              Read More
            </b-button>
          </small>
        </template>
      </b-card>

      <b-card title="WEB APPS DEVELOPMENT"
            img-src="data:image/png;base64,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"
            img-alt="Image"
            img-top
            class="mb-3"
      >
        <b-card-text>
          Ready for Php, Java, & .Net Technology. Performance, security, & user friendly UI are the key that we are concern
        </b-card-text>
        <template v-slot:footer>
          <small class="text-muted">
            <b-button size="sm" variant="info" @click="handleClick">
              Read More
            </b-button>
          </small>
        </template>
      </b-card>

      <b-card title="IOT INTEGRATION"
            img-src="https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcSNufZhJCuAw6P_8sqyKkOV8E-l3xt7-wtVKM9R505nhpoJypBV"
            img-alt="Image"
            img-top
            class="mb-3"
      >
        <b-card-text>
          Internet Of Things (IOT) integration yang kami
          kerjakan adalah koneksi sistem dengan alat alat
          IoT untuk membantu dan memonitor bisnis anda
        </b-card-text>
        <template v-slot:footer>
          <small class="text-muted">
            <b-button size="sm" variant="info" @click="handleClick">
              Read More
            </b-button>
          </small>
        </template>
      </b-card>
    </b-card-group>

    <hr>

    <b-jumbotron
      align-h="center"
      class="text-center"
      bg-variant="info"
    >
      <h3>We design Creative User interface</h3>
      <h3>We develop Smart Mobile Application</h3>
      <h3>We build Secure web back end</h3>
    </b-jumbotron>

    </b-container>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      slide: 0,
      sliding: null
    }
  },
  methods: { onSlideStart (slide) { this.sliding = true }, onSlideEnd (slide) { this.sliding = false } }
}
// data () { return { showDismissibleAlert: false } },
// methods: { handleClick () { this.showDismissibleAlert = true } }
</script>

<style>
@import url('https://fonts.googlelapis.com/css?family=Lato:400,700');
/* #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
body{
  background: #EEF1F4;
  font-family: 'Lato', sans-serif;
}

.height{
  min-height: 10rem;
  background: yellow;
}

.nav-back{
  background: #353535;
}
</style>
