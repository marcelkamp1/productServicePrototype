<template>
  <div>
    <div id="navigation" class="leftX">
      <ul>
        <li>
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
        <h1>Tarife</h1>
      </nav>
      <div>
        <p v-if="$fetchState.pending">
          Fetching posts...
        </p>
        <p v-else-if="$fetchState.error">
          An error occurred :(
        </p>
        <div v-else>
          <h1>Nuxt Posts</h1>
          <table class="spacing">
            <tr>
              <th>ID</th>
              <th>User ID</th>
              <th>Title</th>
            </tr>
            <tr v-for="post in posts" :key="post.id">
              <td>{{ post.id }}</td>
              <td>{{ post.userId }}</td>
              <td>{{ post.title }}</td>
            </tr>
          </table>
          <a class="button--grey" @click="$fetch">
            Refresh
          </a>
        </div>
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
export default {
  data () {
    return {
      posts: []
    }
  },
  async fetch () {
    this.posts = await fetch(
      'https://jsonplaceholder.typicode.com/posts'
    ).then(res => res.json())
  },
  methods: {
    openRouting () {
      if (document.getElementById('content').style.transform === 'translateX(250px)') {
        document.getElementById('content').style.transform = 'translateX(-1px)'
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
  table tr th, table tr td {
    border: 1px solid lightgray;
  }

  table tr th:first-child {
    padding: 0 15px;
  }

  table tr td:last-child {
    text-align: left;
    padding-left: 15px;
  }

  .button--grey {
    cursor: pointer;
  }
</style>
