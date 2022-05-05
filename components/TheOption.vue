<template>
    <select class="select">
        <option value="Русский" v-for="option in mass" :key="option.language">{{ option.name }}</option>
    </select>
</template>

<script>
export default {
    data() {
        return {
            mass: [],
        }
    },
    methods: {
        qwe() {
            console.log(this.mass);
        }
    },
    beforeMount() {
        try {
            const options = {
                method: 'GET',
                headers: {
                    'X-RapidAPI-Host': 'deep-translate1.p.rapidapi.com',
                    'X-RapidAPI-Key': '76d7e06148msh263d850659d08bdp1c483cjsnf26e619a4a8c'
                }
            };

            fetch('https://deep-translate1.p.rapidapi.com/language/translate/v2/languages', options)
                .then(response => response.json())
                .then(response => { this.mass = response.languages; })
                .catch(err => console.error(err));
        } catch (error) {
            console.log(error);
        }
    }
}
</script>

<style>
</style>