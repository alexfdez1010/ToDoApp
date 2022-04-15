<template>
  <div id="quotes-container">
    <h1 id="quotes-title">{{ title }}</h1>
    <div id="quotes-text">
      <p>{{ quote }}</p>
    </div>
    <div id="quotes-author">
      <p>{{ author }}</p>
    </div>
    <button id="quotes-button" @click="getQuote">Nueva cita</button>
  </div>
</template>

<script>
export default {
  name: 'RandomQuotes',
  data() {
    return {
      quote: '',
      author: ''
    }
  },
  props: {
    title: {
      type: String,
      default: 'Famous Quotes'
    }
  },
  methods: {
    getQuote() {
      fetch(`https://api.quotable.io/random`)
          .then(res => res.json())
          .then(data => {
            this.quote = data.content
            this.author = data.author
          })
    }
  },
  beforeMount() {
    this.getQuote()
  }
}
</script>

<style scoped>
#quotes-title{
  margin-top: 5%;
}
#quotes-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 60%;
  height: 100%;
  background: black;
  color: white;
  margin: 2% 20%;
  border-radius: 20px;
}
#quotes-text{
  width: 60%;
  text-align: center;
}

#quotes-button{
  background: #00b300;
  width: 200px;
  height: 50px;
  border-radius: 10px;
  border: 1px solid black;
  color: white;
  font-weight: bold;
  margin-bottom: 5%;
}

</style>