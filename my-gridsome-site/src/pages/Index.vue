<template>
    <Layout>
      <article v-fore="event in agendaEvents" :key="event.uid">

    <h1>{{event.title}}</h1>
     <pre>{{agendaResult}}</pre>
    
    <p>
      Date
       : {{event.dateRange.fr}}
    </p>
       <address>
         {{event.location.name}}<br>
         {{event.location.address}}
         </address>
       </article> 

    </Layout>
</template>
<script>
export default
{
    data(){
        return{
           
            agenda:''
        
        }
    },
   async mounted()
   {
      console.log(process.env.GRIDSOM_AGENDA_URL)
       
       const result =  await fetch("https://${process.env.GRIDSOME_AGENDA_URL}/agendas/${process.env.GRIDSOME_AGENDA_UID}/events.v2.json?key=${process.env.GRIDSOM_AGENDA-KEY.}")
            .then(response=>
             {
                return response.json()
              })
            .then(json => 
            {
              return json
            })
              
            
                this.agenda = result
            },
            computed:
            {
              agendaEvents()
              {
                return this.agenda.envents
              }
            }
        

    }


</script>
