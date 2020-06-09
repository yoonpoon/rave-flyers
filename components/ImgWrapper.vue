
<template>
  <transition name="image-enter">
    <img
      :src="imageUrl"
      :width="this.width ? this.width + 'px' : undefined"
      :height="this.height ? this.height + 'px': undefined"
    >
  </transition>
</template>

<script>
export default {
  props: {
    width: Number,
    height: Number
    // fit: {
    //   type: String,
    //   validator: function(value) {
    //     return ['pad', 'fill', 'scale', 'crop', 'thumb'].indexOf(value) !== -1
    //   }
    // },
    // focus: {
    //   type: String,
    //   validator: function(value) {
    //     return (
    //       [
    //         'center',
    //         'top',
    //         'right',
    //         'left',
    //         'bottom',
    //         'top_right',
    //         'top_left',
    //         'bottom_right',
    //         'bottom_left',
    //         'face',
    //         'faces'
    //       ].indexOf(value) !== -1
    //     )
    //   }
    // },
    // quality: {
    //   type: Number,
    //   validator: function(value) {
    //     return value > 0 && value < 101
    //   }
    // },
    // doubleRes: {
    //   type: Boolean,
    //   default: true
    // },
    // image: {
    //   type: Object,
    //   required: true
    // },
    // backgroundColor: {
    //   type: String
    // }
  },
  data() {
    return {

    }
  },
  computed: {
    // url() {
    //   const url = _get(this.image, 'fields.file.url')
    //   if (url) {
    //     return url
    //   }
    // },
    // imageUrl() {
    //   if (this.url) {
    //     // double dimensions for retina display
    //     const scaleFactor = this.doubleRes ? 2 : 1
    //     return resizedCfImageUrl(this.url, {
    //       width: this.width ? this.width * scaleFactor : null,
    //       height: this.height ? this.height * scaleFactor : null,
    //       fit: this.fit ? this.fit : null,
    //       backgroundColor: this.backgroundColor ? this.backgroundColor : null,
    //       focus: this.focus ? this.focus : null
    //     })
    //   }
    // },
    // imageSrcSet() {
    //   // if no width or height prop is specified the image will use srcset
    //   const widths = [600, 800, 1000, 1250, 1500, 2000, 2500, 3000]
    //   if (this.url && !this.width && !this.height) {
    //     return widths
    //       .map(size => {
    //         return `${this.url}?w=${size} ${size}w`
    //       })
    //       .join(', ')
    //   }
    // },
    // imageAlt() {
    //   return _get(this.image, 'fields.description', '')
    // }
  },
  methods: {}
}
</script>
