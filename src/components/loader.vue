<template>
    <div class="loadFrame">
        <div class="lds-dual-ring"></div>
    </div>
</template>
<style scoped>
.loadFrame{
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    margin-top: 10rem;
}
.lds-dual-ring {
  display: inline-block;
  width: 80px;
  height: 80px;
}
.lds-dual-ring:after {
  content: " ";
  display: block;
  width: 64px;
  height: 64px;
  margin: 8px;
  border-radius: 50%;
  border: 6px solid #4F46E5;
  border-color: #4F46E5 transparent #4F46E5 transparent;
  animation: lds-dual-ring 1.2s linear infinite;
}
@keyframes lds-dual-ring {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

</style>