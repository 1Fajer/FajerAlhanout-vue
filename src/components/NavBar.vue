<template>
  <div class="navbar-container">
    <div class="row px-3 py-2 m-0 w-100">
    
      <div class="col-3 d-flex gap-4 ps-5">
        <i class="bi bi-search"></i>
        <i class="bi bi-toggles2"></i>
      </div>

      
      <div class="col-6"></div>

      
      <div class="col-3 d-flex justify-content-end gap-4 pe-5">
        <i class="bi bi-moon"></i>
        <i class="bi bi-bell-fill"></i>
        <img src="@/assets/England.png" style="width: 30px;height: 30px; border-radius: 50%;" class="mt-1">
        <img src="https://api.dicebear.com/9.x/lorelei/svg?clip=true" style="width: 38px;height: 38px; border-radius: 50%;">
      </div>
    </div>
  </div>
</template>

<style scoped>

.navbar-container {
  position: absolute;
  width: calc(100% - 16.666%);
  top: 0;
  background: white;
  
}


i {
  cursor: pointer;
  transition: color 0.2s ease-in-out;
  color: #8f8f8f;
  font-size: 1.5rem;
}
 

i:hover {
  color: #8964ce; 
}


</style>
