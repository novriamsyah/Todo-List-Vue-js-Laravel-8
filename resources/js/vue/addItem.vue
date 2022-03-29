<template>
    <div class="addItemContainer">
        <input type="text" class="form-control" aria-label="input Item" aria-describedby="input Item" placeholder="Type your todo item" v-model="item.name">
        <font-awesome-icon icon="plus-square" :class="[item.name ? 'active' : 'inactive', 'plus']" @click="addItem()" />
    </div>

</template>

<script>
export default {
    data: function () {
        return {
            item: {
                name: ""
            }
        }
    },
    methods:{
        addItem() {
            if(this.item.name === ''){
                return;
            }

            axios.post('api/item/store', {
                item: this.item
            }).then(response => {
                if(response.status == 201){
                    this.item.name = "";
                    this.$emit('reloadList');
                }
            }).catch(error => {
                console.log(error);
            })
        }
    }
}
</script>

<style scoped>
.addItemContainer{
    display: flex;
    justify-content: center;
    align-items: center;
}

.form-control,
.form-control:focus,
.form-control:active,
.form-control:active:focus {
    min-width: 100%;
    height: 2rem;
    border: none;
    outline: none;
    color: #000000;
    font-weight: bold;
    padding: 5px 10px;
    border-radius: 5px;
    font-size: 16px;
}
.form-control {
  -webkit-box-shadow: none;
          box-shadow: none;
  -webkit-transition: all 0.2s linear;
  transition: all 0.2s linear;
}
.form-control:focus {
  -webkit-box-shadow: 0 0 15px rgba(0,0,0,0.2);
          box-shadow: 0 0 15px rgba(0,0,0,0.2);
}

.plus{
    font-size: 2rem;
    margin-left: 1rem;
    cursor: pointer;
}
.active{
    color: #06f365;
}

.inactive{
    color: #5C5D67;
}
</style>

