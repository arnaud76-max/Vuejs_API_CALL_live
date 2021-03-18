<template>
    <Layout>
        <pre>{{agendaResult}}</pre>
    </Layout>
</template>
<script>
export default{
    data(){
        return{
            AGENDA_URL: 'openagenda.com',
            AGENDA_UID: ' 92222479',
            AGENDA_KEY: 'e6cfdcf18fe644b6a96e880f34c506c4',
            agendaResult:''
        
        }
    },
    methods: {
        apiCall(){
            fetch("https://${this.AGENDA_URL}/agendas/${this.AGENDA_USD}/events.v2.json?key=${this.AGENDA-KEY}")
            .then(function(response) {
                return response.json()
              })
            .then(json => {
                this.agendaResult = json
            })
        }

    }

}
</script>
