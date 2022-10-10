<template>

<div class="container">
    <div class="item">
      <div class="logo">graeme.j.kemp</div>
    </div>
    <div class="item-center">
    </div>
    <div class="item">
    </div>
</div>

</template>

<style scoped>
.container {
  display: flex;
}

.item {
  height: 100px;
  width: 140px; /* A fixed width as the default */
}

.item-center { 
  flex-grow: 1; /* Set the middle element to grow and stretch */
}

.item + .item { 
  margin-left: 2%; 
}

.logo {
  color: #646cff;
  font-weight: 500;
}

</style>