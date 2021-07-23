<template>
    <div>
        <button class="btn btn-success float-right" @click="onNew">
            New Item
        </button>
        <h5>Item View</h5>
        <hr>

        <form action="" @submit.prevent="onSave">
            <b-form-group label="Name">
                <b-form-input v-model="item.name"></b-form-input>
            </b-form-group>
            <b-form-group label="Description">
                <b-form-input v-model="item.description"></b-form-input>
            </b-form-group>
            
            <b-form-group label="Price">
                <b-form-input v-model="item.price"></b-form-input>
            </b-form-group>
            <b-form-group label="Quantity">
                <b-form-input v-model="item.quantity"></b-form-input>
            </b-form-group>

            <b-form-group label="Condition" label-for="condition">
                <b-form-select v-model="item.condition" :options="options"></b-form-select>
            </b-form-group>

            <b-form-group label="Acquired On">
                <b-form-input type="date" v-model="item.acquired_on"></b-form-input>
            </b-form-group>
            <b-form-group>
                <button class="btn btn-primary" type="submit">Save Changes</button>
                <button class="btn btn-danger float-right" type="button" @click="onDelete" v-if="item.id">Delete Item</button>
            </b-form-group>
        </form>
    </div>
</template>

<script>
export default {
    props:{
        item: {},
    },
    
    data() {
        return {
            item: {},
            options: [
                {value: 'good', text: 'New Stock'},
                {value: 'damaged', text: 'No defects'},
                {value: 'lost', text: 'Expired'},
            ]
        }
    },
    methods: {
        async onSave() {
            try {
                if(!this.item.id) {
                    await this.$axios.post('/api/items', this.item)
                }else{
                    await this.$axios.put('/api/items/' + this.item.id, this.item)
                }

                this.$emit('saved')
            } catch (err) {
                alert(err.response.data.message)
            }
        },
        onNew() {
            this.$emit('newItem')
        },
        async onDelete() {
            try {
                this.$axios.delete('/api/items/' + this.item.id)
                this.$emit('deleted')
            } catch (err) {
                alert(err.response.data.message)
            }
        }
    }
}
</script>