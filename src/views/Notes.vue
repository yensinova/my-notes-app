<script setup>
    import { onMounted } from 'vue';
import CreateNote from '../components/CreateNote.vue';
import HeaderComponent from '../components/HeaderComponent.vue';
import NoteCard from '../components/NoteCard.vue';
import { useNoteStore } from '../stores/notes'; 

    const noteStore = useNoteStore(); 

    onMounted(async () => {
        await noteStore.getNotes();
    })
</script>
<template>
    <HeaderComponent />
    <section id="notes-page">
        <h2>Notes</h2>

        <h2 v-if="noteStore.loading">Cargando...</h2>
        <h2 v-if="noteStore.error">Algo ha ido mal</h2>
        <ul v-else class="note-list">
            <li><CreateNote/></li>
            <li v-for="note in noteStore.notes" :key="note.id">
                <NoteCard :note="note"></NoteCard>
            </li>
            <li v-if="!noteStore.notes.length" class="empty-msg">
                <h2>No hay nada que mostrar. Crea tu primera nota</h2>
            </li>
        </ul>
    </section>
</template>
<style>
    #notes-page {
        padding: 40px;
        display: flex;
        flex-direction: column;
        align-items: center;

        .title {
            margin-bottom: 50px;
            text-align: center;
        }

        .note-list {
            background-image: url("/assets/cork.jpg");
            border: 10px solid brown;
            width: 70%;
            min-width: 450px;
            padding: 30px;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 20px;

            .empty-msg {
                text-align: center;
                font-size: 1.5rem;
            }
        }
    }
</style>