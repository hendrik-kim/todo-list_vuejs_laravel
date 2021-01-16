<template>
    <div>
        <div v-for="item in items" :key="item.id">
            <list-item
                :item="item"
                class="item"
                v-on:itemChanged="$emit('reloadList')"
            />
        </div>
    </div>
</template>

<script>
import listItem from "./ListItem";
export default {
    props: ["items"],
    components: { listItem }
};
</script>

<style lang="scss" scoped>
.item {
    background: #e6e6e6;
    padding: 5px;
    margin-top: 5px;
}
</style>
