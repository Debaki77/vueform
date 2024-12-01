
<template>
  <div>
    <div class="table-container" id="table-container">
      <h2 class="text-center mt-5 mb-4">Your submitted Data</h2>
      <table id="dataTable" class="table table-striped">
        <thead>
          <tr>
            <th>S.N</th>
            <th>Name</th>
            <th>Address</th>
            <th>Phone Number</th>
            <th>Email</th>
            <th>Actions</th>
          </tr>
        </thead>

        <tbody id="table-body">
          <tr
            v-if="informations.length < 1"
            class="text-center"
            style="column-span: 8"
          >
        
          </tr>
          <tr v-for="(element, index) in informations" :key="index">
            <td>{{ index + 1 }}</td>
            <td id="table-name">{{ element.name }}</td>
            <td id="table-address">{{ element.address }}</td>
            <td id="table-number">{{ element.phone }}</td>
            <td id="table-email">{{ element.email }}</td>
            <td>
              <button id="edit" @click="$emit('edit',index)"><i class="fa-solid fa-pen-to-square"></i></button>
              <button id="delete" @click="$emit('delete',index)"><i class="fa-solid fa-trash"></i></button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "MyTable",
  props: {
    informations: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
.table-container {
  width: 50%;
  margin: 20px auto;
}

table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 10px;
  background-color: #fff;
  border-radius: 2px;
  margin-bottom: 100px;
}

table,
th,
td {
  border: 1px solid #ccc;
}

th,
td {
  padding: 10px;
  text-align: left;
}
button{
  margin: 5px;
}
#edit{
  color: white;
  background: blue;
}
#delete{
  color: white;
  background: red;
}
#edit:hover{
  color: white;
  background: rgb(60, 60, 184);
}
#delete:hover{
  color: white;
  background: rgb(165, 33, 33);
}
</style> 