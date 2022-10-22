<template>
    <b-container fluid class="my-3 mx-3">
        <template v-if="!loading">
            <h3>My Github Profile</h3>
            <b-row>

                <b-col lg="4">
                    <MainInformationCard :dataFromApi="dataFromApi" />
                    <b-button block @click="getReposFromGithub()" variant="primary">
                        <span v-if="display"> Hide repositories</span>
                        <span v-else> Show repositories</span>
                    </b-button>
                </b-col>

                <b-col lg="8">
                    <template v-if="display">
                        <b-row v-for="(repo, index) in dataRepositoriesFromApi" :key="index">
                            <b-col lg="8" class="mt-2">
                                <RepositoryCard :repo="repo" />
                            </b-col>
                        </b-row>
                    </template>
                    <template v-else>
                        <b-alert variant="warning" class="mt-3" show>Please click on "Show repositories"</b-alert>
                    </template>
                </b-col>

            </b-row>
        </template>
        <template v-else>
            <b-spinner label="Spinning"></b-spinner>
        </template>
    </b-container>
</template>
  
<script>
import axios from "axios";
import RepositoryCard from './RepositoryCard.vue'
import MainInformationCard from './MainInformationCard.vue'

export default {
    name: 'GithuProfile',
    components: {
        RepositoryCard,
        MainInformationCard
    },

    data: () => ({
        url: "https://api.github.com/users/alexsantm2019",
        urlRepos: "https://api.github.com/users/alexsantm2019/repos",
        dataFromApi: [],
        dataRepositoriesFromApi: [],
        display: false,
        loading: false
    }),

    methods: {
        //Función principal para extraer datos de API de github
        async getProfileFromGithub() {
            this.loading = true;
            await axios.get(this.url)
                .then((result) => {
                    this.dataFromApi = result.data;
                });
            this.loading = false;
        },
        //Función que extrae datos de los repositorios
        async getReposFromGithub() {
            this.display = !this.display;
            await axios.get(this.urlRepos)
                .then((result) => {
                    this.dataRepositoriesFromApi = result.data;
                });
        },
    },
    created() {
        //Lanzo la función al momento de cargar la página
        this.getProfileFromGithub();
    },
}
</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
    margin: 40px 0 0;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    display: inline-block;
    margin: 0 10px;
}

a {
    color: #42b983;
}
</style>
  