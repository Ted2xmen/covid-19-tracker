<template>
<div class="text-3xl">
    {{text}} 
    <div class="text-2xl">
        {{timeStamp}} 
    </div>
</div>
</template>
<script>
import moment from 'moment';

export default {
    name: 'DataTitle',
    props: ['text', 'dataDate'],
    computed: {
        timeStamp : function () {
            return moment(this.dataDate).format('MMMM Do YYYY, h:mm:ss a')
        }
    }
}
</script>