<template>
    <div class="advantage-item" v-bind:class="{'is-complete': advantage.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete">
            {{advantage.title}}
            <button @click="$emit('del-advantage', advantage.id)" class="del">x</button>
        </p>
    </div>
</template>

<script>
export default {
    name: "AdvantageItem",
    props: ["advantage"],
    methods: {
        markComplete(){
            this.advantage.completed = !this.advantage.completed
        }
    }
}
</script>

<style scoped>
    .advantage-item{
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }
    .is-complete{
        text-decoration: line-through;
    }
    .del{
        background: #ff0000;
        color: #fff;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>