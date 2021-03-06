<template>
  <div class="facts">
    <!-- Bootstrap vue navbar -->
    <b-navbar toggleable="sm" type="light" variant="light">
      <b-navbar-toggle target="nav-text-collapse"></b-navbar-toggle>
      <!-- Emoji with route to / -->
      <b-navbar-brand>
        <nuxt-link class="navbar-brand" to="/"
          ><span style="font-size: 100px">&#128049;</span></nuxt-link
        >
      </b-navbar-brand>
      <!-- Router links with current page emphasized -->
      <b-collapse id="nav-text-collapse" is-nav>
        <b-navbar-nav>
          <nuxt-link class="nav-item nav-link" to="/"
            >Home<span class="sr-only">(current)</span></nuxt-link
          >
          <nuxt-link class="nav-item nav-link" to="/images">Images</nuxt-link>
          <nuxt-link class="nav-item nav-link active" to="/facts"
            >Facts<span class="sr-only">(current)</span></nuxt-link
          >
          <nuxt-link class="nav-item nav-link" to="/social">Social</nuxt-link>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>

    <!-- Page heading using named slot -->
    <div id="page-heading">
      <page-heading>
        <h1
          slot="page-title"
          class="font-weight-light text-center text-lg-left mt-4 mb-0"
          style="margin-left: 1rem"
        >
          Cat Facts
        </h1>
      </page-heading>
    </div>

    <!-- v-for iteration over an array of fact objects -->
    <b-card
      v-for="(fact, index) in facts"
      :key="fact.title"
      no-body
      class="mb-1"
    >
      <b-card-header header-tag="header" class="p-1" role="tab">
        <b-button v-b-toggle="'accordion-' + index" block variant="info">{{
          fact.title
        }}</b-button>
      </b-card-header>
      <b-collapse
        :id="'accordion-' + index"
        accordion="my-accordion"
        role="tabpanel"
      >
        <!-- Card body -->
        <b-card-body>
          <b-card-text>{{ fact.body }}</b-card-text>
        </b-card-body>
      </b-collapse>
    </b-card>
  </div>
</template>

<script>
// Importing PageHeading component to enable slot
import PageHeading from '@/components/PageHeading.vue'

export default {
  // Registering imported components
  components: {
    PageHeading,
  },
  data() {
    return {
      // Array declation of fact objects
      facts: [
        {
          title: 'Cats Can Make Over 90 Different Sounds',
          body:
            'Meow! Grrrr! Hisss! These are some of the noises we typically associate with cats. One of the most surprising cat facts is that cats can actually make almost 100 different sounds. From the peeps of kittens to the meows of adults, cats have a wide range of vocalizations. Kittens typically meow to their mother for milk, but most adult cats are only known to meow in the presence of humans. Cat owners must be seen as cat parents after all! Scientific studies of the noises cats make have mostly centered on classifying the various sounds. Some scientists have sought to learn the truth behind one of the most mysterious cat facts – just how do cats purr? The rhythmic vibration of the purr comes from the cat’s throat, but, as yet, there is no agreement on how exactly the sound is made. Do you ever get the feeling your cats are talking to you? Maybe they are! Cats have been known to imitate the sounds of human babies in order to attract the attention of their owner. They can also recognize the sound of their owner’s voice. However, cats lack the advanced mental capabilities of humans that enable language. So don’t worry – you’re still smarter than your cat.',
        },
        {
          title: 'Lions, Tigers, Jaguars, and Leopards Purr Too',
          body:
            'When we think of purring, we often think of house cats, but big cats like cheetahs and mountain lions also purr. Even tigers, lions, jaguars, and leopards sometimes make a purr-like sound when they exhale. The roar of a lion is actually closely associated with the purring sound all cats make. The ability of one species of cat to purr and another species to roar is based on their anatomy, including specific features of the vocal folds and the length of the vocal tract.',
        },
        {
          title: 'There Are Exactly 24 Whiskers On Every Cat',
          body:
            'Cat’s whiskers are another amazing feature of their anatomy. There are exactly 24 whiskers on a cat, 12 on each side of their face. Cats use their whiskers for hunting and for sensing their surroundings. Veterinary neuroscientists have established some incredible cat facts relating to whiskers. A cat’s whiskers connect to a part of their brain that is similar to the visual cortex. This means that cats can almost see with their whiskers. When hunting in close quarters, a cat’s whiskers will point towards their prey. It’s also been shown that cats with damaged whiskers have difficulty catching their prey. Those whiskers are more than just a fashion statement! Cats also use their whiskers to sense whether or not they can fit into a tight space.',
        },
        {
          title: 'Milk Is Not Good For Cats! Most Cats Are Lactose Intolerant',
          body:
            'Some people think that feeding cats milk is good for them. This supposed cat fact is really a myth. Perhaps it’s all those cartoons we’ve seen featuring kittens lapping up milk from saucers, but cats are actually lactose intolerant and feeding them cow’s milk is not good for their digestive system. It’s true, however, that kittens need milk in order to survive. The best milk a kitten can have is the milk from its own mother. When a kitten is orphaned, there is special kitten formula you can use to ensure the kitten develops into a healthy adult cat. Despite the myth, cow’s milk doesn’t have the right set of nutrients to help a kitten grow. While some cats are not lactose intolerant, the very best thing for all cats to drink is fresh water.',
        },
      ],
    }
  },
  head() {
    return {
      title: 'Cat facts',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Random cat facts hosted on interesting-facts.com',
        },
      ],
    }
  },
}
</script>
