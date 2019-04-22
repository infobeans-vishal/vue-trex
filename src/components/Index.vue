<template>
    <div>
        <Header></Header>
        <Footer></Footer>
    </div>
</template>


<script>

import Header from './Header'
import Footer from './Footer'
import Content from './Content'


export default {
    props: {
      source: String
    },
    components: {
        Header,
        Footer,
        Content
    }
}
</script>

