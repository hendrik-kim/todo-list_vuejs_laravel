<template>
    <div class="item">
        <input
            type="checkbox"
            @change="updateStatus()"
            v-model="item.completed"
        />
        <span :class="[item.completed ? 'completed' : '', 'itemText']">
            {{ item.name }}
        </span>
        <button @click="removeItem()" class="remove">
            X
        </button>
    </div>
</template>

<script>
export default {
    props: ["item"],
    methods: {
        updateStatus() {
            axios
                .put("api/item/" + this.item.id, {
                    item: this.item
                })
                .then(res => {
                    if (res.status === 200) {
                        this.$emit("itemChanged");
                    }
                })
                .catch(err => {
                    console.log(errr);
                });
        },
        removeItem() {
            axios
                .delete("api/item/" + this.item.id)
                .then(res => {
                    if (res.status === 200) {
                        this.$eimit("itemChanged");
                    }
                })
                .catch(err => {
                    console.log(err);
                });
        }
    },
    created() {
        console.log("List Item : " + this.item);
    }
};
</script>

<style lang="scss" scoped>
.completed {
    text-decoration: line-through;
    color: #999999;
}
.itemText {
    width: 100%;
    margin-left: 20px;
}
.item {
    display: flex;
    justify-content: center;
    align-items: center;
}
.remove {
    color: #fff;
    background: #000;
}
</style>
