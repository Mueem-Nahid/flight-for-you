<template>
    <div>
        <ul>
            <li v-for="info in infoes" :key="info">
                {{info}}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props: {
        infoes: {
            type: Array
        }
    }
}
</script>
