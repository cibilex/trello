<template>
  <q-page padding>
    <div class="row">
      <div class="col-sm-4 col-xs-12"></div>
      <div class="col-sm-8 col-xs-12  q-pa-sm">
        <div id="favorite-boards">
                    <div class="q-gutter-x-md">
                    <q-icon name="far fa-star" size="sm"></q-icon>
                    <span class="text-h6" style="vertical-align:sub;">Star Boards</span>
          </div>
          <div class="row q-mt-sm">
            <board v-for="board in favoriteBoards" :key="board.id" class="q-mr-sm q-mb-lg rounded-borders q-pa-sm" :board="board" />
          </div>
        </div>
                <div id="last-visited" class="q-mt-md">
                    <div class="q-gutter-x-md">
                    <q-icon name="workspaces" size="sm"></q-icon>
                    <span class="text-h6" style="vertical-align:sub;">Workspaces</span>
          </div>
          <div class="row q-mt-sm">
            <board v-for="board in otherBoards" :key="board.id" class="q-mr-sm q-mb-lg rounded-borders q-pa-sm" :board="board" />
            <create-board class="q-mr-sm q-mb-lg rounded-borders q-pa-sm"></create-board>
          </div>
        </div>
      </div>
    </div>
  </q-page>
</template>

<script>
import Board from 'components/Board.vue';
import { defineComponent } from 'vue';
const boards=[
  {
    id:1,
    title:"My Board",
    description:"board description",
    bgColor:"red",
    color:"yellow",
    is_favorite:true
  },
    {    id:2,
    title:"sadas",
    description:"board description",
    bgColor:"green",
    color:"accent",
    is_favorite:false
  },
    {    id:3,
    title:"My Board",
    description:"board description",
    bgColor:"yellow",
    color:"positive",
    is_favorite:true
  },
    {    id:4,
    title:"My Board",
    description:"board description",
    bgColor:"primary",
    color:"dark ",
    is_favorite:true
  }, {    id:4,
    title:"My Board",
    description:"board description",
    bgColor:"primary",
    color:"dark ",
    is_favorite:true
  },
    {    id:5,
    title:"My Board",
    description:"board description",
    bgColor:"dark",
    color:"secondary",
    is_favorite:false
  }
]
import {ref} from "vue"
import CreateBoard from "components/CreateBoard"
export default defineComponent({
  components: { Board,CreateBoard },
  name: 'PageIndex',
  setup(){
    const favoriteBoards=ref(boards.filter((board)=>board.is_favorite==true))
    const otherBoards=ref(boards.filter((board)=>board.is_favorite !=true))
    return{
      boards,
      favoriteBoards,
      otherBoards
    }
  }
})
</script>
