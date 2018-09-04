<template>
  <div>
    <v-data-table
      :headers="headers"
      :items="desserts"
      class="elevation-1"
    >
      <template slot="headerCell" slot-scope="props">
        <v-tooltip bottom>
          <span slot="activator">
            {{ props.header.text }}
          </span>
          <span>
            {{ props.header.text }}
          </span>
        </v-tooltip>
      </template>
      <template slot="items" slot-scope="props">
        <td>{{ props.item.a_username }}</td>
        <td class="text-xs-left">{{ props.item.a_password }}</td>
        
      </template>
    </v-data-table>
 
  </div>
</template>
<script>
export default {
  data () {
    return {
      headers: [
        {
          text: 'ชื่อผู้ใช้',
          align: 'left',
          sortable: false,
          value: 'name',
        },
        { text: 'Email', value: 'Email' },
   
        
      ],
      desserts: [],
    }
  },
async created() {
  // เรียกใช้งาน
    this.getstudent()
  }, 
methods: {
    async getstudent() {
      let res = await this.$http.get('http://127.0.0.1/php-thada/student.php')
      this.desserts = res.data.student 
      // ตัวแปล
    },
}
}
</script>