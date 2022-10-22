<template>
    <b-container>

        <b-card
        border-variant="primary"
        :header="repo.name"
        header-bg-variant="primary"
        header-text-variant="white"
        align="center"
      >

      <b-list-group>
                <b-list-group-item class="d-flex justify-content-between align-items-center">
                    Name:
                    <span>{{repo.full_name}}</span>
                </b-list-group-item>
                <b-list-group-item class="d-flex justify-content-between align-items-center">
                    Private:
                    <span>{{repo.private}}</span>
                </b-list-group-item>     
                <b-list-group-item class="d-flex justify-content-between align-items-center">
                    Url:
                    <span><a :href="repo.owner.url">Click here to go to respository</a></span>
                </b-list-group-item>   
                <b-list-group-item class="d-flex justify-content-between align-items-center">
                    Language:
                    <span>{{repo.language}}</span>
                </b-list-group-item>            
                <b-list-group-item class="d-flex justify-content-between align-items-center">
                    Created at:
                    <span>{{repo.created_at}}</span>
                </b-list-group-item> 

            </b-list-group>
      

      </b-card>

    </b-container>
  </template>
  
  <script>
  export default {
    name: 'RepositoryCard',
    props: ['repo'] 
  }
  </script>
  