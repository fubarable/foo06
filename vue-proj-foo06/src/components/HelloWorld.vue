<script setup>
import { ref } from 'vue';

defineProps({
  msg: {
    type: String,
    required: true,
  },
});

const cssLinks = ref([
  {
    text: 'CSS Grid',
    tutLink: 'https://css-tricks.com/snippets/css/complete-guide-grid/',
    tutLinkLabel: 'CSS Grid Tutorial',
  },
  {
    text: 'FlexBox',
    tutLink: 'https://css-tricks.com/snippets/css/a-guide-to-flexbox/',
    tutLinkLabel: 'FlexBox Tutorial',
  },
  {
    text: '@media CSS',
    tutLink: 'https://developer.mozilla.org/en-US/docs/Web/CSS/@media',
    tutLinkLabel: '@media Tutorial',
  },
]);
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h3>
      Created to try to find out the CSS that divides the screen in two as this app is doing. It uses CSS Grid for the
      #app and then uses flexbox for smaller sub-items.
    </h3>
    <div class="tutLinks">
      <fieldset>
        <legend>For More On:</legend>
        <div class="linkGrid">
          <div v-for="cssLink in cssLinks" :key="cssLink.text" class="oneLink">
            <span class="foo">
              {{ cssLink.text }}:
            </span>
            <span class="bar">
              <a :href="cssLink.tutLink" target="_blank">{{
                cssLink.tutLinkLabel
              }}</a>
            </span>
          </div>
        </div>
      </fieldset>
    </div>
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

.tutLinks {
  margin: 10px;
  text-align: left;
}

.oneLink {
  display: grid;
  grid-template-columns: 1fr 2fr;
}
</style>
