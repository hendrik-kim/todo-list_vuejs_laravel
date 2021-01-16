<template>
    <div class="container">
        <input type="text" v-model="item.name" /><button
            @click="addItem()"
            :disabled="item.name ? false : true"
        >
            Submit
        </button>
    </div>
</template>

<script>
export default {
    name: "AddItemForm",
    data() {
        return {
            item: {
                name: ""
            }
        };
    },
    methods: {
        addItem() {
            if (this.item.name == "") {
                return;
            }
            console.log("click");

            axios
                .post("api/item/store", {
                    item: this.item
                })
                .then(res => {
                    if (res.status == 201) {
                        this.item.name == "";
                    }
                })
                .catch(err => {
                    console.log(error);
                });
        }
    }
};
</script>

<style lang="scss" scoped>
.container {
    display: flex;
    justify-content: center;
    align-items: center;
}
input {
    background: #f7f7f7;
    border: 0px;
    outline: none;
    padding: 5px;
    margin-top: 10px;
    width: 100%;
}
button {
    font-size: 15px;
}
</style>
