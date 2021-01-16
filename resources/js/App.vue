<template>
    <div class="container">
        <header>This is Vue Laravel Todo List</header>
        <add-item-form />
        <list-view />
    </div>
</template>

<script>
import AddItemForm from "./components/AddItemForm";
import ListView from "./components/ListView";

export default {
    name: "App",
    components: { AddItemForm, ListView }
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
