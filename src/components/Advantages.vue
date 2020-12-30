<template>
    <div>
        <div v-for="advantage in advantages" :key="advantage.id">
            <AdvantageItem v-bind:advantage="advantage" v-on:del-advantage="$emit('del-advantage', advantage.id)"/>
        </div>
    </div>
</template>

<script>
import AdvantageItem from "./AdvantageItem.vue"

export default {
    name: "Advantages",
    props: ["advantages"],
    components: {
        AdvantageItem
    }
}

</script>

<style scoped>

</style>>