<template>
  <section>
    <transition-group name="list" tag="ul">
      <li v-for="(todoItem, index) in propsdata" :key="todoItem" class="shadow"> <!-- key 속성을 주는게 v-for때 좋 -->
        <i class="checkBtn fa fa-check" aria-hidden="true"></i>
        {{todoItem}}
        <span class="removeBtn" type="Button" @click="removeTodo(todoItem, index)"> <!-- @click와 v-on:click는 동일 -->
          <i class="far fa-trash-alt" aria-hidden="true"></i>
        </span>
      </li>

    </transition-group>
  </section>
</template>

<script>
export default{
  props: ['propsdata'],
  methods:{
    removeTodo(todoItem, index){
      this.$emit('removeTodo', todoItem, index) //emit 메서드. 이벤트, 인자1, 인자2. 전달받은 인자 값은 상위 컴포넌트에서 변경하면 안된다. 하위 컴포넌트에 반영이 안되기 때문
    }
  }
}
</script>


<style>
  ul{
    list-style-type: none;
    padding-left: 0px;
    margin-top: 0;
    text-align: left;
  }
  li{
    display: flex;
    min-height: 50px;
    line-height: 50px;
    height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius: 5px;
  }
  .checkBtn{
    line-height: 45px;
    color: #62acde;
    margin-right: 5px;
  }
  .removeBtn{
    margin-left: auto;
    color: #de4343;
  }

  .list-item{
    display: inline-block;
    margin-right: 10px;
  }
  .list-move{
    transition: transform 1s;
  }

  .list-enter-active, .list-leave-active {
    transition: all 1s;
  }
  .list-enter, .list-leave-to {
    opacity: 0;
    transform: translateY(30px);
  }
</style>