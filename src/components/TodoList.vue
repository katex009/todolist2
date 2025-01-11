<script setup lang="ts">
    import ListItem from './ListItem.vue';
    type Item = {
        title: string;
        checked?: boolean;
    }
    const items: Item[] = [
        {title: 'leer un libro al mes', checked: true},
        {title: 'hacer ejercicio', checked: false},
        {title: 'aprender algo nuevo'},
];
</script>

<template>
    <ul>
        <li :key="index" v-for="(item, index) in items">
            <ListItem :isChecked="item.checked">
                {{ item.title }}
            </ListItem>

        </li>
    </ul>
</template>

<style scoped>

</style>