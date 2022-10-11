<script setup>
import {reactive} from 'vue'
import InputNew from './InputNew.vue';

const boards = reactive([
    {
        id: crypto.randomUUID(),
        name: 'tablero 1',
        items: [
            {
                id: crypto.randomUUID(),
                title: 'Feature de archivos',
            },
            {
                id: crypto.randomUUID(),
                title: 'Resolver bug',
            }
        ]
    }, 

    {
        id: crypto.randomUUID(),
        name: 'tablero 2',
        items: [
            {
                id: crypto.randomUUID(),
                title: 'Mandar reporte',
            },
            {
                id: crypto.randomUUID(),
                title: 'Code review',
            }
        ]
    }
]);


function handleNewItem(text){
    console.log(text.value)
}

</script>

<template>
    <nav>
        <ul>
            <li>
                <a href="#">create board</a>
            </li>
        </ul>
    </nav>
    <div class="boards-container">
        <div class="boards">
            <div class="board" v-for="board in boards" :key="board.id">
                <div> {{board.name}} </div>
                <InputNew @on-new-item="handleNewItem"/>
                <div class="items">
                    <div class="item" v-for="item in board.items" :key="item.id"> {{item.title}} </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>

.boards{
    display: flex;
    gap: 10px;
}
.board{
    background: #efefef;
    padding: 10px;
}
.items{
    display: flex;
    flex-direction: column;
    gap: 5px;
}
.item{
    background-color: white;
    padding: 10px;
    box-sizing: border-box;
}


</style>

