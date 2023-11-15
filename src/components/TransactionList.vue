<template>
    <h3>History</h3>
    <ul id="list" class="list">
        <!-- <li class="minus">
            Cash <span>-Rp 4,000</span><button class="delete-btn">X</button>
        </li>
        <li class="plus">
            Paycheck <span>+Rp 7,000</span><button class="delete-btn">X</button>
        </li> -->
        <li v-for="transaction in transactions" v-bind:key="transaction.id" :class="transaction.amount < 0 ? 'minus' : 'plus'">
            {{ transaction.text }} <span>Rp {{ transaction.amount }}</span><button @click="deleteTransaction(transaction.id)" class="delete-btn">X</button>
        </li>
    </ul>
</template>

<script setup>
    import { defineProps } from "vue";

    const emit = defineEmits(['transactionDeleted'])

    const props = defineProps({
        transactions:{
            type: Array,
            requred: true
        }
    })

    const deleteTransaction = (id) => {
        emit('transactionDeleted', id);
    }
</script>