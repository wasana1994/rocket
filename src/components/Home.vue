<template>
    <div class="row">
      <div class="col-sm-12">
        <h1 class="text-center">Rocket Project</h1>
      </div>
      <div class="col-sm-12">
        <ul>
          <li v-for="item in launchList" :key="item.id">
            {{ item.name }},{{item.date_local}}
          </li>
        </ul>
      </div>
    </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      launchList: [],
    }
  },
  created(){
    this.axios.get('https://api.spacexdata.com/v4/launches')
    .then(response => {
      // JSON responses are automatically parsed.
      this.launchList = response.data
    })
    .catch(e => {
      this.errors.push(e)
    })
  },
  mounted(){

  },
  methods: {
    
  }
}
</script>