<script>
export default {
  props: {
    msg: String,
    appName: String,
  },
  data() {
    return {
      books: ["Anime", "Jute"],
      novels: [
        {
          id: 1,
          title: "Bad Man",
          author: "Guest",
        },
        {
          id: 2,
          title: "Live along",
          author: "Mark Noton",
        },
      ],
      library: {
        id: "1",
        name: "Juna",
        location: "heuston",
        payment: "card",
      },
    };
  },
  computed: {
    hasPublishedBooks() {
      return this.books.length > 0 ? "Yes" : "No";
    },
  },
  methods: {
    enterClicked() {
      alert("Enter clicked, @keyup.enter directive used");
    },
    clearBookList() {
      this.books.length == 0
        ? (this.books = ["Anime", "Jute"])
        : (this.books = []);
      return this.books;
    },
  },
};
</script>

<template>
  <div class="greetings">
    <h1 class="green">
      {{ msg }} {{ appName }}
      {{ "hello,message".split(",").reverse().join("") }}
    </h1>
    <p>{{ hasPublishedBooks }}</p>
    <p>demoing v-for on a list of objects</p>
    <ul v-for="novel in novels" :key="novel.id">
      <li>
        {{ novel.title }}
      </li>
    </ul>
    <p>demoing v-for on an object</p>
    <ul v-for="value in library" :key="value.index">
      <li>
        {{ value }}
      </li>
    </ul>
    <button :disabled="false" v-on:click.prevent="clearBookList">
      Disabled Button
    </button>
    <input @keyup.enter="enterClicked" />
    <h3>
      You’ve successfully created a project with
      <a href="https://vitejs.dev/" target="_blank" rel="noopener">Vite</a> +
      <a href="https://vuejs.org/" target="_blank" rel="noopener">Vue 3</a>.
    </h3>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
