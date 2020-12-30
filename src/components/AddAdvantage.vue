<template>
    <div>
        <form @submit="addAdvantage">
            <input type="text" v-model="title" name="title" placeholder="Adicionar vantagem">
            <input type="submit" value="Adicionar" class="btn">
        </form>
    </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';

export default {
    name: "AddAdvantage",
    data() {
        return{
            title: ''
        }
    },
    methods: {
        addAdvantage(e) {
            e.preventDefault();
            const newAdvantage = {
                id: uuidv4,
                title: this.title,
                completed: false
            }
            this.$emit("add-advantage", newAdvantage);
            this.title='';
        }
    }
}

</script>

<style scoped>
    form{
        display: flex;
    }
    input[type="text"]{
        flex: 10;
        padding: 5px;
    }
    input[type="submit"]{
        flex: 2;
    }
</style>