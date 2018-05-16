<template>
   <div id="Toggle__parent">
      <div id="Toggle__label">
         <slot></slot>
      </div>
      <div id="Toggle__container" @click="toggle" ref="toggle-container">
         <div id="Toggle__slider" :style="{ left: visible === true ? '50%' : '0%' }" />
         <div id="Toggle__on" class="Toggle__side">
            <span>On</span>
         </div>

         <div id="Toggle__off" class="Toggle__side">
            <span>Off</span>
         </div>
      </div>
   </div>
</template>

<script>
export default {
   props: {
      visible: {
         type: Boolean,
         required: true
      }
   },
   methods: {
      toggle() {
         this.$emit('toggle')
      }
   }
}
</script>

<style scoped>
#Toggle__parent {
   display: flex;
   align-items: center;
}

#Toggle__label {
   margin-right: 15px;
}

#Toggle__container {
   display: flex;
   border-radius: 3px;
   /* border: 1px solid #F2F2F2; */
   height: 25px;
   width: 100px;
   position: relative;
   cursor: pointer;
}

#Toggle__slider {
   position: absolute;
   top: 0;
   left: 50%;
   height: 100%;
   width: 50%;
   background-color: #f2f2f2;
   transition: 250ms;
}

.Toggle__side {
   border: 1px solid #f2f2f2;
   box-sizing: border-box;
   width: 50%;
   height: 100%;
   display: flex;
   justify-content: center;
   align-items: center;
}

#Toggle__on {
   background-color: #2aabe2;
}

#Toggle__off {
   background-color: #f2f2f2;
   color: black;
}
</style>
