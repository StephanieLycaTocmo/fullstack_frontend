<template>
    <div>
        <NavBar />
        <div class="container">
            <h1>My Items</h1>
            <div class="row">
                <div class="col-6">
                    <h5>List of Items</h5>
                    <hr>
                    <ul class="list-group">
                        <li class="list-group-item btn-li"  v-for="item in items" :key="item.id" @click="onSelected(item)">
                            {{item.name}} <span class="float-right">{{item.price}}</span>
                        </li>
                    </ul>
                </div>
                <div class="col-4">
                    <ItemView :item="selectedItem" @saved="onChange" @newItem="onNew" @deleted="onChange" />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            items: [],
            selectedItem: {}
        }
    },
    methods: {
        async getMyItems() {
            await this.$axios.get('/api/items')
            .then((res)=>{
                if(res.status==200) {
                    this.items = res.data
                }
            })
        },
        onChange() {
            this.getMyItems()
            this.selectedItem = {}
        },
        onSelected(item) {
            this.selectedItem = item;
        },
        onNew() {
            this.selectedItem = {}
        },
    },
    created() {
        this.getMyItems()
    }
}
</script>

<style>
h1 {
    text-align: center;
    margin-top: 25px;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}
.buttons {
    text-align: center;
}
</style>