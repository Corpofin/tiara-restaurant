<template>
<nav class="navbar fixed-top navbar-expand-sm navbar-light w-100" v-bind:class="{'bg-white': scrollPosition > headerHeight}" data-aos="fade-down" data-aos-duration="300">
  <router-link class="navbar-brand" to="/">
    <img class="d-inline-block align-top" src="../assets/img/logo.png" alt="Logo" width="30" height="30"/>

    <span class="cursive font-weight-bold name">Tiara's</span>
  </router-link>

  <button class="border-0 navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">

    <span class="navbar-toggler-icon"></span>
  </button>

  <div class="collapse navbar-collapse" id="navbarSupportedContent">
    <ul class="navbar-nav text-right ml-auto w-auto">
      <li class="nav-item" v-for="(item, index) in menu" v-bind:key="index">
        <router-link exact class="nav-link mx-2 pb-1 px-0" v-bind:to="to(item)">
          {{ item.label || item }}
        </router-link>
      </li>
    </ul>
  </div>
</nav>
</template>

<script>
export default {
  data() {
    return {
      menu: [
        {
          to: "/",
          label: "Home"
        },
        "Reservations",
        "Contact"
      ],
      scrollPosition: 0,
      headerHeight: 0
    };
  },
  mounted() {
    window.addEventListener("scroll", this.updateScroll);
    window.addEventListener("resize", this.updateSize);
  },
  methods: {
    to(input) {
      if (input.label) {
        return input.to;
      } else {
        return `/${input.toLowerCase()}`;
      }
    },
    updateScroll() {
      this.scrollPosition = window.scrollY;
    },
    updateSize() {
      this.headerHeight = document.getElementById("header").clientHeight;
    }
  }
};
</script>

<style lang="scss" scoped>
.name {
  letter-spacing: 0.125rem;
}
</style>
