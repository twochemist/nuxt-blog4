<template>
  <client-only>
    <resume
      class="cv"
      :segments="segments"
      :skills="skills"
      :information="information"
      :settings="settings"
    />
  </client-only>
</template>

<script>
import resume from 'vue-resume-component'
import segments from '@/content/cv/segments.json'
import skills from '@/content/cv/skills.json'
import information from '@/content/cv/information.json'
import settings from '@/content/cv/settings.json'
import getSiteMeta from 'assets/js/getMeta'
export default {
  name: 'Cv',
  layout: 'cv',
  components: {
    resume,
  },
  data() {
    return {
      segments,
      skills,
      information,
      settings,
    }
  },
  computed: {
    meta() {
      const metaData = {
        title: `CV - ${this.globals.title}`,
        description: 'My personal CV as a website.',
        url: `/cv`,
        img: `/luka_harambasic_cv.png`,
        imgAlt: `CV - ${this.globals.title}`,
      }
      return getSiteMeta(metaData)
    },
  },
  head() {
    return {
      title: this.meta.title,
      meta: [...this.meta],
      link: [
        {
          hid: 'canonical',
          rel: 'canonical',
          href: `${this.globals.baseURL}/cv`,
        },
      ],
    }
  },
}
</script>

<style lang="sass" scoped>
.cv
  @media (prefers-color-scheme: dark)
    border-radius: $border-radius
    border: 1px solid $color-dark
</style>
