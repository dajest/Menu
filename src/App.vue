<template>

  <div class="wrap">
    <div class="week-list">

      <div class="single-week-area" v-for="singleWeek in weeks" :key="singleWeek.weekNumber">
        <h1>Неделя - {{singleWeek.weekNumber}}</h1>
        <draggable
          class="dragArea list-group"
          :list="singleWeek.dishesAdded"
          group="dishes"
          @change="log"
        >
        <div
          class="list-group-item"
          v-for="(dish, idx) in singleWeek.dishesAdded"
          :key="idx"
        >
          {{ dish.name }}
        </div>
        </draggable>
      </div>


    </div>
    <div class="dish-list">
      <draggable
        class="dragArea list-group"
        :list="list2"
        :group="{ name: 'dishes', pull: 'clone', put: false }"
        @change="log"
      >
        <div
          class="list-group-item"
          v-for="element in list2"
          :key="element.name"
        >
          {{ element.name }}
        </div>
      </draggable>
    </div>
  </div>

</template>

<script>
import draggable from "vuedraggable";
export default {
  name: "clone",
  display: "Clone",
  order: 2,
  components: {
    draggable
  },
  data() {
    return {
      weeks: [
        {
          weekNumber: 1,
          dishesAdded: []
        },
        {
          weekNumber: 2,
          dishesAdded: []
        },
        {
          weekNumber: 3,
          dishesAdded: []
        }, 
        {
          weekNumber: 4,
          dishesAdded: []
        }, 
        {
          weekNumber: 5,
          dishesAdded: []
        }, 
        {
          weekNumber: 6,
          dishesAdded: []
        }, 
        {
          weekNumber: 7,
          dishesAdded: []
        }, 
        {
          weekNumber: 8,
          dishesAdded: []
        }      
      ],
      list1: [],
      list2: [
        { name: "Борщ", id: 1 },
        { name: "Рассольник", id: 2 },
        { name: "Щавелёвый", id: 3 },
        { name: "Гречка", id: 4 },
        { name: "Рис", id: 5 },
        { name: "Паста", id: 6 },
        { name: "Свинина", id: 7 },
        { name: "Говядина", id: 8 },
        { name: "Курица", id: 9 },
        { name: "Рыба", id: 10 },
      ]
    };
  },
  methods: {
    log: function(evt) {
      window.console.log(evt);
    }
  }
};
</script>
<style lang="scss">

.wrap {
  display: grid;
  grid-template-columns: 4fr 1fr;
  grid-column-gap: 20px;
}

.week-list, .dish-list {
  box-sizing: border-box;
  border: 1px solid darkcyan;
  padding: 20px;
  height: 100%;
}

.week-list {
  display: grid;
  grid-template-columns: repeat(4,1fr);
  grid-gap: 10px;
  
  .single-week-area {
    box-sizing: border-box;
    border: 1px solid darkgray;
    min-height: 200px;
    display: flex;
    flex-direction: column;
    // box-shadow: 1px 0px 26px -1px rgba(34, 60, 80, 0.21);

    h1 {
      font-size: 20px;
      text-align: center;
      margin: 0;
      border-bottom: 1px solid darkgray;
    }
    
    .dragArea.list-group {
      box-sizing: border-box;
      padding: 20px;
      // background-color: darkred;
      flex: 1;
    }

    .list-group-item {
      margin-bottom: 5px;

      &:last-child {
        margin: 0;
      }
    }
  }
  
}



.list-group-item {
    position: relative;
    display: block;
    padding: 0.75rem 1.25rem;
    margin-bottom: -1px;
    background-color: #fff;
    border: 1px solid rgba(0,0,0,.125);
  cursor: move;
}

.list-group-item:first-child {
    border-top-left-radius: 0.25rem;
    border-top-right-radius: 0.25rem;
}
</style>
