// 使用graphql查询预存的数据
<template>
  <Layout>
    <div>
      <h1>Posts2</h1>
      <ul>
        <li v-for="edge in $page.posts.edges" :key="edge.node.id">
          <g-link :to="edge.node.path">{{ edge.node.title }}</g-link>
        </li>
      </ul>
    </div>
  </Layout>
</template>

<page-query>
 query{
   posts: allPost{
    edges{
      node{
        id
        title
        path
      }
    }
  }
}
</page-query>

<script>
export default {};
</script>

<style>
</style>