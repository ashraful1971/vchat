<template>
    <div class="chatitem" @click="itemClicked">
        <div class="item-image">
            <img src="../assets/logo.png" alt="Picture">
        </div>
        <div class="item-content">
            <h4>John Doe</h4>
            <p>this was the last mesasage.</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ChatItem',
    data: function(){
        return {}
    },
    methods: {
        itemClicked(){
            this.$emit('itemClick');
        }
    }
}
</script>

<style scoped>
    .chatitem {
        width: 100%;
        display: flex;
        flex-direction: row;
        align-items: center;
        cursor: pointer;
    }
    .chatitem:hover {
        background-color: #f8f8f8;
    }
    .chatitem .item-image {
        margin-right: 10px;
    }
    .chatitem .item-image img {
        width: 50px;
        height: 50px;
        object-fit: cover;
        border-radius: 50%;
        border: 2px solid #000;

    }

    .chatitem .item-content {
        width: 100%;
        text-align: left;
        padding: 20px 0;
        border-bottom: 1px solid rgba(204, 204, 204, 0.349);
    }
    .chatitem .item-content h4 {
        display: block;
        margin: 0 0 5px;
    }
    .chatitem .item-content p {
        display: block;
        margin: 0;
        color: #555;
    }
</style>