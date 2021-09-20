<template>
    <table>
  <thead>
    <tr>
      <th v-for="key in columns" :key="key.id">
        {{key | capitalize}}
      </th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="entry in data" :key="entry.id">
      <td v-for="key in columns" :key="key.id">
        {{entry[key]}}
      </td>
    </tr>
  </tbody>
</table>
</template>

<script>

export default {
    name:'Grid'
}
</script>
