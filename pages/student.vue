<template>
<v-app>
   <v-form v-model="valid"> 
    <v-text-field
      v-model="name"
      :rules="nameRules"
      :counter="10"
      label="Name"
      required  
    ></v-text-field>
    <v-text-field
      v-model="email"
      :rules="emailRules"
      label="E-mail"
      required
    ></v-text-field>
  </v-form>
    <div class="text-xs-center">
    <v-btn color="blue" dark @click="Dologin">login</v-btn> 
    <nuxt-link to="/"><v-btn color="yellow" dark @click="Dosave">cancel </v-btn></nuxt-link>
  </div>
  
  </v-app>
</template>

<script>
  export default {
    layout : "publics",
    data: () => ({ //แหล่งเก็บชื่อตัวแปร
      valid: false,
      name: '',
      nameRules: [
        v => !!v || 'Name is required',
        v => v.length <= 20 || 'Name must be less than 10 characters'
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(v) || 'E-mail must be valid'
      ]
    }),
    methods:{
      async Dologin(){
        console.log (this.email)
        console.log (this.password)
        let res = await this.$http.post('http://127.0.0.1/php-thada/login.php', {
          user : this.name,
          pass : this.email
        })
        if (res.data.ok){
          this.$router.push('/table')
        }
      },
      Dosave(){
        this.name='',
        this.email=''
      }
    }
  }
</script>