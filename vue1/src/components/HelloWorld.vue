<script>
export default {
  props: ['msg'],
  data() {
    return {
      timerId: -1,
      currentTextIndex: 0,
      text: '',
      greetingTexts: [
        'You’ve successfully created a project',
        'Vue’s official documentation provides you with all information you need to get started',
        'Got stuck? Ask your question on Vue Land, our official Discord server, or StackOverflow',
        'As an independent project, Vue relies on community backing for its sustainability. You can help us by becoming a sponsor',
      ]
    }
  },
  mounted() {
    this.text = this.greetingTexts[0];
    this.timerId = setTimeout(this.changeText, 2000);
  },
  unmounted() {
    clearTimeout(this.timerId);
  },
  methods: {
    changeText() {
      clearTimeout(this.timerId);
      this.currentTextIndex++;
      if (this.currentTextIndex == this.greetingTexts.length) this.currentTextIndex = 0;
      this.text = this.greetingTexts[this.currentTextIndex];
      this.timerId = setTimeout(this.changeText, 2000);
    }
  }
}
</script>

<template>
  <div class="greetings">
    <h1 class="green" @click="changeText">{{ msg }}</h1>
    <h3>
      {{ timerId }}
      {{ text }}
    </h3>
  </div>
</template>

<!-- <style scoped>
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
</style> -->
