<script setup lang="ts">
    import { ref } from 'vue';
    import type { Ref } from 'vue';
    import ListItem from './ListItem.vue';
    type Item = {
        title: string;
        checked?: boolean;
    }
    const GroupsItems: Ref<Item[]> = ref([
        {title: 'leer un libro al mes', checked: true},
        {title: 'hacer ejercicio', checked: false},
        {title: 'aprender algo nuevo'},
]);

    const updateItem = (element: Item): void => {
        const updateItem = findItemList(element)
        if (updateItem) {
            toggleItemCheck(updateItem)
        }
    }

    const findItemList = (element: Item): Item | undefined => {
        return GroupsItems.value.find((elementItemInList) => elementItemInList.title === element.title)
    }

    const toggleItemCheck = (element: Item): void => {
        element.checked = !element.checked
    }
</script>

<template>
    <ul>
        <li :key="index" v-for="(element, index) in GroupsItems">
            <ListItem :isChecked="element.checked" @updateItem="updateItem(element)">
                {{ element.title }}
            </ListItem>

        </li>
    </ul>
</template>

<style scoped>

</style>