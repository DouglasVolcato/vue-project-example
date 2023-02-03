<template>
    <div>
        <h2>{{ title }}</h2>
        <input :class="{ 'green-border': fruitInput !== '', 'red-border': fruitInput === '' }" v-model="fruitInput" />
        <button @click="handleClick">Add fruit</button>
        <br>
        <div v-show="isDivShown">
            <span>{{ message }}</span>
        </div>
        <div>
            <ul>
                <li v-for="fruit in fruits" :key="fruit.name">
                    {{ fruit.name }}
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: "TestComponent",
    props: {
        title: String
    },
    data() {
        return {
            isDivShown: false,
            fruitInput: "",
            fruits: [
                { name: 'Apple' },
                { name: 'Banana' },
                { name: 'Orange' }
            ]
        }
    },
    methods: {
        handleClick() {
            this.fruits.push({ name: this.fruitInput })
            this.fruitInput = ""
        }
    }
}
</script>

<style scoped>
.green-border {
    border: solid 5px green;
    background-color: rgb(202, 255, 202);
}

.red-border {
    border: solid 5px red;
    background-color: rgb(255, 198, 198);
}

ul {
    list-style-type: none;
}
</style>