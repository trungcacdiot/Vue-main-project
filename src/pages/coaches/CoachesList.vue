<template>
    <section>
        FILTER
    </section>
    <section>
        <base-card>
        <div class="controls">
            <base-button mode="outline">Refresh</base-button>
            <base-button link to="/register">Register as Coach</base-button>
        </div>
      <ul v-if="hasCoaches">
         <coaches-item v-for="coach in filteredCoaches"
                     :key="coach.id" 
                     :id="coach.id"
                     :first-name="coach.firstName"
                     :last-name="coach.lastName"
                     :rate="coach.hourlyRate"
                     :areas="coach.areas"
                     ></coaches-item>
        </ul>
        <h3 v-else> No coachs found. </h3>
        </base-card>
    </section>
    
</template>

<script>
import CoachesItem from "../../components/coaches/CoachesItem";

export default {
    components: {
        CoachesItem
    },
    computed: {
        filteredCoaches() {
            return this.$store.getters['coaches/coaches'];
        },
        hasCoaches(){
            // console.log(this.$store.getters['coaches/coaches'].length)
            // console.log(this.$store.getters['coaches/hasCoaches'])
            return this.$store.getters['coaches/hasCoaches'];
        }
    }
}
</script>

<style scoped>
    ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

.controls {
  display: flex;
  justify-content: space-between;
}
</style>
