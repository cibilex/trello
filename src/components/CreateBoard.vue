<template>
<div class="col-xs-5 col-sm-4 col-md-3 text-indigo-9 cursor-pointer bg-grey-4 relative-position" :class="$attrs.class" v-ripple style="height:85px;" @click="dialogModel=true">
  <div class="absolute-center full-width text-center">Create new Board</div>
</div>
  <q-dialog   v-model="dialogModel" position="top"  transition-hide="fade-in"  transition-show="slide-down">
    <q-card flat  class="transparent full-width q-mt-xl ">
      <div class="row justify-center" style="max-width:500px;">
        <div class="box column justify-aroun3 rounded-borders q-pa-sm  relative-position" :class="`bg-${currentColor}`" style="width:296px;height:auto;">
          <q-icon name="close" color="red" class="absolute-top-right q-ma-sm cursor-pointer" style="z-index:2;" v-close-popup  size="xs"></q-icon>
          <div class="row full-width">
            <div class="col-auto">
               <q-input  placeholder="add board title"  v-model="boardTitleModel" @focus="bgColor='rgba(215, 219, 221 ,0.4)'" @blur="bgColor=''" :input-style="{backgroundColor:bgColor}"  class="no-padding inputHoverEffect"  input-class="text-grey-3 text-bold rounded-borders q-pa-xs" dense borderless></q-input>
            </div>
          </div>
          <div class="text-white">trello clone</div>
          
          <div class="row full-width">
            <div class="col-auto">
                        <q-select dark v-model="selectModel" dense  :style="{backgroundColor:selectBgColor}" @focus="selectBgColor='rgba(215, 219, 221 ,0.4)'" @blur="selectBgColor=''" borderless    class="q-px-xs inputHoverEffect  no-shadow rounded-borders selectLabel"    :options="options" >
            <template v-slot:selected>
                           <q-item dense class="text-white">
                  <q-item-section >
                    <div>
                     <q-icon :name="selectModel.icon" size="14px" class="q-mr-md" color="white"></q-icon> {{selectModel.value}}
                    </div>
                  </q-item-section>
                </q-item>
            </template>
                    <template v-slot:option="scope">
          <q-item v-bind="scope.itemProps" class="bg-white text-dark">
                              <q-item-section >
                    <div>
                     <q-icon :name="scope.opt.icon" size="14px" class="q-mr-md" :color="scope.opt.iconColor"></q-icon> {{scope.opt.label}}
                    </div>
                    <q-item-label caption class="q-mt-sm text-dark text-grey-7">{{scope.opt.description}}</q-item-label>
                  </q-item-section>
          </q-item>
        </template>
          </q-select>
            </div>
          </div>
        </div>
        <div class="flex-break q-my-sm lt-md"></div>
        <div class="q-mt-xs" :class="[{'row justify-center':$q.screen.lt.md},{'col':$q.screen.gt.md}]" style="width:296px;" >
                  <q-btn  class="bg-negative col-2 q-ma-xs" v-for="color in colors" :key="color" :class="`bg-${color}`" @click="currentColor=color" :icon="currentColor==color? 'done' : undefined" :style="$q.screen.lt.md ? 'height:50px;width:50px;' : 'height:20px;width:20px;'"></q-btn>
        </div>
      </div>
      <div class="row justify-center">
        <div class="col-3">
          <q-btn label="Create" class="q-mt-sm" v-close-popup no-caps :disable="boardTitleModel ? false : true"  :color="boardTitleModel ? 'blue-7' : 'grey-4'" :text-color="boardTitleModel ? 'white' : 'indigo-3'"></q-btn>
        </div> 
      </div>
    </q-card>
  </q-dialog>
</template>

<script>
import {ref} from "vue"
const options=[
  {
    label:"Private",
    value:"private",
    description:"Board and trello clone workspace members can see and edit this board.",
    icon:"lock",
    iconColor:"red-6"
  },  {
    label:"Wokspace",
    value:"workspace",
    description:"All members of trello clone workspace can see and edit it.<",
    icon:"people",
    iconColor:"grey-7"
  },  {
    label:"Open for everybody",
    value:"open for everybody",
    description:"everybody in internet can see and edit it.",
    icon:"public",
    iconColor:"green"
  },

]
const colors=["green-5","red-5","yellow-5","deep-orange-5","purple-5","blue-5","indigo-5","pink-5","brown-5","grey-5","blue-grey-5","lime-5"]
export default {
  // name: 'ComponentName',

  setup () {
    return {dialogModel:ref(false),bgColor:ref(""),selectModel:ref({icon:"lock",value:"private"}),selectBgColor:ref(""),options:ref(options),boardTitleModel:ref(""),colors,currentColor:ref("blue-5")}
  }
}
</script>

<style scoped>
label.selectLabel .q-field__native.row.items-center{
  padding: 0px !important;
}label.selectLabel .q-item.q-item-type{
  padding: 0px !important;
}
.inputHoverEffect:hover{
  background-color:rgba(215, 219, 221 ,0.2);
}
</style>