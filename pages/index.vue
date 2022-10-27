<template>
  <Tutorial/>
</template>

<script>
export default {
  data(){
    return {
      appID: '378921147650387',
      appSecret: 'cfd3091effdcf6313216ab12a83ad67e',
      redirectURI: 'http://localhost:3000/',
      stateParams: "{st=state123abc,ds=123456789}"
    }
  },
  name: 'IndexPage',
  methods: {
    async callLoginDialogue(){
      try {
        const response = await this.$axios.$get(`https://www.facebook.com/v15.0/dialog/oauth?client_id=${this.appID}&redirect_uri=${this.redirectURI}&state=${this.stateParams}`, 
        { headers: { 'Content-Type': 'application/json'}})
        console.log('Hey this from facebook login endpoint: ', response)
      } catch (error) {
        
      }
    }
    
  },
  created(){
    this.callLoginDialogue()
  }
}

</script>
