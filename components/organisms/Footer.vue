<template lang="pug">
  footer.footer
    footer-logo
    p.copyright &copy;
      | naomoon
</template>

<script>
import Footerlogo from '@/assets/images/svg/logo.svg'

export default {
  name: 'Footerlogo',
  components: {
    Footerlogo
  }
}
</script>

<style　lang="scss" scope>
.footer {
  width: 100%;
  height: auto;
  text-align: center;
  background: darken($key, 8%);
  padding: 40px 0;
  color: $white;
}

.copyright {
  font-size: 0.6rem;
}
</style>
