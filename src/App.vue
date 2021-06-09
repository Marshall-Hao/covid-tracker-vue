<template>
<Header />
  <div class="container mt-0 xl:mt-10 self-center">
    <router-view/>
  </div>
</template>

<script>
import Header from '@/components/Header'

export default {
  components: {
    Header
  }
}
</script>
