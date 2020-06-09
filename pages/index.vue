<template>
  <client-only>
    <section
      v-if="allPosts && postCount"
      @click="loadMorePosts"
      v-masonry
      transition-duration=".65s"
      item-selector=".item"
      class="masonry-container"
    >
      <img
        v-for="post in allPosts"
        v-masonry-tile
        class="item"
        :key="post.id"
        :src="post.image.url"
      />
    </section>
  </client-only>
  <!-- <client-only>
    <div
      v-masonry
      transition-duration=".2s"
      item-selector=".item"
      class="masonry-container"
    >
      <img
        v-for="image in images"
        v-masonry-tile
        class="item"
        :key="image.ix"
        :src="require('@/assets/' + image.src)"
      />
    </div>
  </client-only> -->
</template>

<script>
import gql from 'graphql-tag'

const POSTS_PER_PAGE = 1

const allPosts = gql`
  query allPosts($first: IntType, $skip: IntType) {
    allPosts(first: $first, skip: $skip) {
      id
      title
      image {
        url
      }
    }
    _allPostsMeta {
      count
    }
  }
`

export default {
  data() {
    return {
      loading: 0
    }
  },
  apollo: {
    $loadingKey: 'loading',
    allPosts: {
      query: allPosts,
      variables() {
        return {
          skip: 0,
          first: POSTS_PER_PAGE
        }
      }
    },
    postCount: {
      query: allPosts,
      update: ({ _allPostsMeta }) => _allPostsMeta.count
    }
  },
  methods: {
    loadMorePosts() {
      this.$apollo.queries.allPosts.fetchMore({
        variables: {
          skip: this.allPosts.length
        },
        updateQuery: (previousResult, { fetchMoreResult }) => {
          if (!fetchMoreResult) {
            return previousResult
          }
          return Object.assign({}, previousResult, {
            allPosts: [...previousResult.allPosts, ...fetchMoreResult.allPosts]
          })
        }
      })
    }
  }
}
</script>
