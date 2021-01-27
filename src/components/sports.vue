<template>
  <div class="sports">
    <h1 class="card-header">Sports listing</h1>
    <section v-if="errored">
      <p>Nous sommes désolés, nous ne sommes pas en mesure de récupérer ces informations pour le moment.
      Veuillez réessayer ultérieurement.</p>
    </section>

    <section class="card-body" v-else>
      <div v-if="loading">
        <p>Chargement...</p>
      </div>

        <div
            v-else
            v-for="sport in info"
            :key="sport.idSport"
            class="row">
          <div class="col-sm-6 m-auto">
            <div class="card">
              <div class="card-body">
                <h5 class="card-title">{{ sport.strSport }}</h5>
                <div class="container"><img :src="sport.strSportThumb" alt=""></div>
                <p class="text-muted">{{ sport.strFormat }}</p>
                <p class="card-text">{{ sport.strSportDescription }}</p>
              </div>
            </div>
          </div>
        </div>
    </section>

  </div>
</template>

<script>
import axios from 'axios'
export default {
name: "sports",
  data(){
    return{
      info : null,
      loading: true,
      errored: false
    }
  },

  mounted(){
    axios
      .get('https://www.thesportsdb.com/api/v1/json/1/all_sports.php')
      .then(response => {
          this.info = response.data.sports
      })
      .catch(error => {
        this.errored = true
        console.log(error)
      })
      .finally(() => {
        this.loading = false
      })
  }
}
</script>

<style scoped>

</style>