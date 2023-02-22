<template>
    <div class="content">
        <main class="py-4">
            <div class="container-fluid" id="app">
                <div class="row">
                    <div class="col-md-8 col-12">
                        <div class="grid row">

                                <div class="grid-item" v-for="artwork in artworks" :key="artwork.id">
                                    <a data-fancybox="gallery" data-fancybox-title="artwork.title" :href='"/images/gallery/"+artwork.file'>
                                        <span class="fancybox-title">{{ artwork.title }}</span>
                                        <img :src='"/thumbnail/"+artwork.file' :alt="artwork.file" :title="artwork.title">
                                        {{ artwork.title }}
                                    </a>
                                </div>

                        </div>

                        <div class="row paginate">

                        </div>
                    </div>
                </div>
            </div>
        </main>
    </div>
</template>

<script>
    export default {
          data: function() {
              return {
                  artworks: []
              }
          },
          mounted() {
              this.loadArtwork()
          },
          methods: {
              loadArtwork: function() {
                  //load API
                  axios.get('https://photos.jbiddulph.com/api/artwork')
                  .then((response) => {
                      this.artworks = response.data
                  })
                  .catch( function (error) {
                      console.log(console.log("Here is the error ZZ: ",error))
                  })
                  //assign this.artwork
              }
          }
    }
</script>
