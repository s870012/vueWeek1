<script setup>
import { ref } from 'vue'
const data = [
  {
    id: 1,
    name: '珍珠奶茶',
    description: '香濃奶茶搭配QQ珍珠',
    price: '50',
    qty: '20',
  },
  {
    id: 2,
    name: '冬瓜檸檬',
    description: '清新冬瓜配上新鮮檸檬',
    price: '45',
    qty: '18',
  },
  {
    id: 3,
    name: '翡翠檸檬',
    description: '綠茶與檸檬的完美結合',
    price: '55',
    qty: '34',
  },
  {
    id: 4,
    name: '四季春茶',
    description: '香醇四季春茶，回甘無比',
    price: '45',
    qty: '10',
  },
  {
    id: 5,
    name: '阿薩姆奶茶',
    description: '阿薩姆紅茶搭配香純鮮奶',
    price: '50',
    qty: '25',
  },
  {
    id: 6,
    name: '檸檬冰茶',
    description: '檸檬與冰茶的新清結合',
    price: '45',
    qty: '20',
  },
  {
    id: 7,
    name: '芒果綠茶',
    description: '芒果與綠茶的茶特風味',
    price: '55',
    qty: '18',
  },
  {
    id: 8,
    name: '抹茶拿鐵',
    description: '抹茶的鮮奶的搭配',
    price: '60',
    qty: '20',
  },
]
const drinks = ref(data)

const addQty = (id) => {
  drinks.value = drinks.value.map((drink) => {
    if (drink.id === id) {
      drink.qty++
    }
    return drink
  })
}

const minusQty = (id) => {
  drinks.value = drinks.value.map((drink) => {
    if (drink.id === id && drink.qty > 0) {
      drink.qty--
    }
    return drink
  })
}
</script>

<template>
  <div class="container">
    <table>
      <thead>
        <tr>
          <th scope="col">品項</th>
          <th scope="col">描述</th>
          <th scope="col">價格</th>
          <th scope="col">庫存</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="drink in drinks" :key="drink.id">
          <td>{{ drink.name }}</td>
          <td>{{ drink.description }}</td>
          <td>{{ drink.price }}</td>
          <td>
            <button v-on:click="minusQty(drink.id)" :disabled="drink.qty < 1">-</button>
            {{ drink.qty }}
            <button v-on:click="addQty(drink.id)">+</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped></style>
