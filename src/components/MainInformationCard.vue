<template>
    <b-container fluid>

        <b-card :title="dataFromApi.name" :img-src="dataFromApi.avatar_url" 
            img-alt="Image" 
            img-top tag="article"
            class="mb-2 ">

            <b-list-group>
                <b-list-group-item class="d-flex justify-content-between align-items-center">
                    Login
                    <span>{{dataFromApi.login}}</span>
                </b-list-group-item>

                <b-list-group-item class="d-flex justify-content-between align-items-center">
                    Url:
                    <span><a :href="dataFromApi.html_url">Link to repository</a></span>
                </b-list-group-item>

                <b-list-group-item class="d-flex justify-content-between align-items-center">
                    Location:
                    <span>{{dataFromApi.location}}</span>
                </b-list-group-item>
                <b-list-group-item class="d-flex justify-content-between align-items-center">
                    Repos:
                    <span>{{dataFromApi.public_repos}}</span>
                </b-list-group-item>
            </b-list-group>

            <b-card-text class="mt-2 text-justify">
                {{dataFromApi.bio}}
            </b-card-text>
        </b-card>

    </b-container>
  </template>
  
  <script>
  export default {
    name: 'MainRepositoryCard',
    props: ['dataFromApi'] 
  }
  </script>
  