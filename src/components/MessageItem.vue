<template>
    <div class="messageitem" :class="[sideClass]">
        <p><slot></slot></p>
    </div>
</template>

<script>
export default {
    name: 'MessageItem',
    props: {
        side: Number
    },
    data: function(){
        return {

        }
    },
    computed: {
        sideClass(){
            if(this.side == 1){
                return 'left'
            } else if(this.side == 2) {
                return 'right'
            } else {
                return 'error-2'
            }
        }
    }
}
</script>

<style scoped>
    .messageitem {
        display: flex;
        flex-direction: column;
    }
    .left {
        align-items: start;
    }
    .left p {
       align-items: end;
       background-color: #fff;
    }
    .right {
       align-items: end;
    }
    .right p {
       align-items: end;
       background-color: #DCF8C6;
    }
    .messageitem p {
        text-align: left;
        font-size: 15px;
        padding: 15px 10px;
        margin: 10px;
        width: 60%;
        border-radius: 3px;
        color: #333;
    }
</style>