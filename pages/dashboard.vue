<template>
  <div>
    <div id="navigation" class="leftX">
      <ul>
        <li>
          <!-- use NuxtLink for internal routing as a placement for the a-tag -->
          <!-- a-tags should link to external sources -->
          <NuxtLink to="./dashboard">
            <img src="~/assets/images/dashboard.png" class="icon"></img>
            Dashboard
          </NuxtLink>
        </li>
        <p>Marketing Variants</p>
        <li>
          <NuxtLink to="./tariffs">
            <img src="~/assets/images/steuerfrei.png" class="icon"></img>
            Tarife
          </NuxtLink>
        </li>
        <li>
          <NuxtLink to="#">
            <img src="~/assets/images/server.png" class="icon"></img>
            Hardware
          </NuxtLink>
        </li>
      </ul>
    </div>
    <div id="content" class="container containerPosition rightX">
      <nav class="navbar">
        <img src="~/assets/images/hamburger.png" @click="openRouting"></img>
        <h1>Dashboard</h1>
      </nav>
      <section class="dashboardButtons">
        <Telekom class="logo" />
        <a href="./tariffs" class="button--magenta">Tarife</a>
        <a href="./#" class="button--magenta">Hardware</a>
      </section>
    </div>
    <Footer />
  </div>
</template>

<script>
export default {
  methods: {
    openRouting () {
      if (document.getElementById('content').style.transform === 'translateX(250px)') {
        document.getElementById('content').style.transform = 'translateX(0px)'
        document.getElementById('navigation').style.transform = 'translateX(-250px)'
        document.getElementById('footer').style.width = '100%'
      } else {
        document.getElementById('content').style.transform = 'translateX(250px)'
        document.getElementById('navigation').style.transform = 'translateX(0px)'
        document.getElementById('footer').style.width = '128%'
      }
    }
  }
}
</script>

<style>
  .container {
    min-height: 90vh;
  }
</style>
