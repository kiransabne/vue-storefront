<template>
  <div>
    Core product row
  </div>
</template>

<script>
import AddToCart from 'core/components/AddToCart.vue'
import { productThumbnailPath } from 'core/helpers'

export default {
  name: 'Product',
  props: {
    product: {
      type: Object,
      required: true
    }
  },
  computed: {
    thumbnail () {
      const thumbnail = productThumbnailPath(this.product)
      if (typeof navigator !== 'undefined' && !navigator.onLine) {
        return this.getThumbnail(thumbnail, 310, 300) // for offline support we do need to have ProductTile version
      } else return this.getThumbnail(thumbnail, 150, 150)
    }
  },
  components: {
    AddToCart
  }
}
</script>
