<template>
    <div class="container">
        <header>This is Vue Laravel Todo List</header>
        <add-item-form />
        <list-view v-bind:items="items" v-on:reloadList="getList()" />
    </div>
</template>

<script>
import AddItemForm from "./components/AddItemForm";
import ListView from "./components/ListView";

export default {
    name: "App",
    components: { AddItemForm, ListView },
    data: function() {
        return {
            items: []
        };
    },
    methods: {
        getList() {
            axios
                .get("api/items")
                .then(res => {
                    this.items = res.data;
                })
                .catch(err => {
                    console.log(err);
                });
        }
    },
    created() {
        this.getList();
        console.log("App : " + this.items);
    }
};
</script>

<style lang="scss" scoped>
.container {
    width: 350px;
    margin: auto;
}

header {
    background: #e6e6e6;
    padding: 10px;
    text-align: center;
}
</style>
