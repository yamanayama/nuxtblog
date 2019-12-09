<template lang="pug">
  .container
    .gridLines
      .gridWrapper
        .grid
          .line(v-for="line of 6" :key="line") &nbsp;
    Header
    main
      nuxt
      Footer
</template>


<script>
;(function(d) {
  var config = {
      kitId: 'slt8asq',
      scriptTimeout: 3000,
      async: true
    },
    h = d.documentElement,
    t = setTimeout(function() {
      h.className = h.className.replace(/\bwf-loading\b/g, '') + ' wf-inactive'
    }, config.scriptTimeout),
    tk = d.createElement('script'),
    f = false,
    s = d.getElementsByTagName('script')[0],
    a
  h.className += ' wf-loading'
  tk.src = 'https://use.typekit.net/' + config.kitId + '.js'
  tk.async = true
  tk.onload = tk.onreadystatechange = function() {
    a = this.readyState
    if (f || (a && a != 'complete' && a != 'loaded')) return
    f = true
    clearTimeout(t)
    try {
      Typekit.load(config)
    } catch (e) {}
  }
  s.parentNode.insertBefore(tk, s)
})(document)
</script>

<script>
import Header from '@/components/organisms/Header.vue'
import Footer from '@/components/organisms/Footer.vue'

export default {
  components: {
    Header,
    Footer
  }
}
</script>


<style lang="scss" scope>
main {
  width: 98%;
}

.container {
  position: relative;
}

.gridLines {
  height: 100%;
  position: absolute;
  width: 100%;
  z-index: -9999;
  overflow: hidden;
}
.gridWrapper {
  position: relative;
  width: 100%;
  height: 100%;
  left: -50%;
}

.grid {
  width: 1920px;
  position: relative;
  left: -960px;
  display: block;
  height: 100%;
  float: left;
  margin-left: 100%;
}

.line {
  background: #dddddd;
  height: 100%;
  width: 1px;
  float: left;
  margin-left: 323px;
}

@include md {
  main {
    width: 100%;
  }
}
</style>
