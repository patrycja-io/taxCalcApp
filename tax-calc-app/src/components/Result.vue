<template>
  <div>
    <table>
      <tr class="table-head">
        <th class="name">Name</th>
        <th class="value">Value</th>
      </tr>
      <tr
        v-for='element in results'
        :key="element.label"
      >
        <td>{{element.label}}</td>
        <td class="value">
          {{element.value}}
        </td>
      </tr>
    </table>

    <button
      v-on:click="handleBackClick"
      class="btn-back"
    >
      Back
    </button>
  </div>
</template>