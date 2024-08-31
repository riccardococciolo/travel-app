<script>
export default {
    data() {
        return {
            isEditing: true,
            form: {
                title: this.title || '',
                description: this.description || '',
                date: this.date || '',
                city: this.city || '',
                image: this.image || null
            }
        };
    },
    methods: {
        edit() {
            this.isEditing = true;
        },
        save() {
            this.isEditing = false;
        },
        cancel() {
            this.isEditing = false;
        },
        onFileChange(event) {
            const file = event.target.files[0];
            if (file) {
                console.log('File selected:', file);
                this.form.image = URL.createObjectURL(file);
            } else {
                console.log('No file selected');
            }
        }
    },

};
</script>

<template>
    <div class="card p-4 m-5">
        <div v-if="!isEditing">
            <h3 class="py-2">{{ form.title }}</h3>
            <p class="py-2">{{ form.description }}</p>
            <p class="py-2"><strong>Data:</strong> {{ form.date }}</p>
            <p class="py-2">{{ form.city }}</p>
            <div class="py-2" v-if="form.image">
                <img :src="form.image" alt="Immagine del viaggio" width="100" />
            </div>
            <button @click="edit">Modifica</button>
        </div>

        <div v-else>
            <form @submit.prevent="save">
                <div>
                    <label class="pe-3" for="title">Titolo:</label>
                    <input v-model="form.title" type="text" id="title" required />
                </div>
                <div class="py-3">
                    <label class="pe-3" for="description">Descrizione:</label>
                    <textarea v-model="form.description" id="description" required></textarea>
                </div>
                <div class="py-3">
                    <label class="pe-3" for="date">Data:</label>
                    <input v-model="form.date" type="date" id="date" required />
                </div>
                <div class="py-3">
                    <label class="pe-3" for="title">Luogo:</label>
                    <input v-model="form.city" type="text" id="title" required />
                </div>
                <div class="py-3">
                    <label class="pe-3" for="image">Immagine:</label>
                    <input type="file" @change="onFileChange" />
                </div>
                <button class="me-3" type="submit">Salva</button>
                <button class="pe-3" type="button" @click="cancel">Annulla</button>
            </form>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.card {
    border: 1px solid #ddd;
    border-radius: 1rem;
    margin-bottom: 20px;
    width: 400px;
    box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.1);
}
</style>