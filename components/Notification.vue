<template>
    <div class="w-full p-3 text-lg text-center text-gray-800 border-2 rounded-xl dark:text-gray-300"
        :class="{'border-red-500' : type === 'danger', 'border-green-500' : type === 'success'}">
        {{message}}
    </div>
</template>
<script>
export default {
    props: ['message', 'type']
}
</script>