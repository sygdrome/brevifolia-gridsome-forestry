<template>
  <Layout page="test">
    <section class="info__blurb">
      <div v-html="data.description"></div>
      <div v-html="data.cta"></div>
      <ul>
        <li>
          <p>
            <a :href="`mailto:${data.contact.email}`">
              Email: {{ data.contact.email}}
            </a>
          </p>
        </li>
        <li>
          <p>
            <a :href="`https://twitter.com/${data.contact.twitter_handle}`">
              Twitter: @{{ data.contact.twitter_handle}}
            </a>
          </p>
        </li>
        <li>
          <p>
            <a :href="`https://github.com/${data.contact.github_handle}`">
              Github: {{ data.contact.github_handle }}
            </a>
          </p>
        </li>
      </ul>
    </section>
  </Layout>
</template>
<script>
  export default {
    metaInfo() {
      return {
        title: "Test",
        bodyAttrs: {}
      }
    },
    computed: {
      data: function () {
        return this.$page.metadata.testData
      }
    }
  }
</script>
<page-query>
    query getInfoPageData {
        metadata {
            testData {
                description
                cta
                contact {
                    email
                    twitter_handle
                    github_handle
                }
                background_color
                text_color
            }
        }
    }
</page-query>