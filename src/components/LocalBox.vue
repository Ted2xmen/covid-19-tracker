<template>
    <div class="grid md:grid-cols-1 gap-4 p-4 m-4">
        <!-- box 1 -->
        <div class="shadow-xl text-center rounded p-7 bg-blue-600">
            <h3 class="font-bold text-3xl p-1 m-1">
                {{localTitle}}
            </h3>
            <span class="font-bold">New: </span>
            Local box new
            <br>
            <span class="font-bold">Total: </span>
            local box total
        </div>
    </div>
</template>
<script>
export default {
    name: 'LocalBox',
    props: ['localTitle'],
    
}
</script>