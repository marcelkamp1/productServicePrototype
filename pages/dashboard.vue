<template>
  <div>
    <div id="navigation" class="leftX">
      <ul>
        <li>
          <a href="./dashboard">
            <img src="~/assets/images/dashboard.png" class="icon"></img>
            Dashboard
          </a>
        </li>
        <p>Marketing Variants</p>
        <li>
          <a href="./tariffs">
            <img src="~/assets/images/steuerfrei.png" class="icon"></img>
            Tarife
          </a>
        </li>
        <li>
          <a href="#">
            <img src="~/assets/images/server.png" class="icon"></img>
            Hardware
          </a>
        </li>
      </ul>
    </div>
    <div id="content" class="container containerPosition rightX">
      <nav class="navbar">
        <img src="~/assets/images/hamburger.png" @click="openRouting"></img>
        <h1>Dashboard</h1>
      </nav>
      <Logo />
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
      } else {
        document.getElementById('content').style.transform = 'translateX(250px)'
        document.getElementById('navigation').style.transform = 'translateX(0px)'
      }
    }
  }
}
</script>

<style>
  .container {
    min-height: 89vh;
  }
</style>
