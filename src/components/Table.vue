<template>
  <div>
    <a-table v-mScroll="'.ant-table-scroll .ant-table-body'" :columns="columns" :data-source="data" :scroll="{ x: 1500, y: 300 }">
      <a slot="action" slot-scope="text">action</a>
    </a-table>
  </div>
</template>
<script>
const columns = [
  { title: 'Full Name', width: 100, dataIndex: 'name', key: 'name', fixed: 'left' },
  { title: 'Age', width: 100, dataIndex: 'age', key: 'age', fixed: 'left' },
  { title: 'Column 1', dataIndex: 'address', key: '1', width: 150 },
  { title: 'Column 2', dataIndex: 'address', key: '2', width: 150 },
  { title: 'Column 3', dataIndex: 'address', key: '3', width: 150 },
  { title: 'Column 4', dataIndex: 'address', key: '4', width: 150 },
  { title: 'Column 5', dataIndex: 'address', key: '5', width: 150 },
  { title: 'Column 6', dataIndex: 'address', key: '6', width: 150 },
  { title: 'Column 7', dataIndex: 'address', key: '7', width: 150 },
  { title: 'Column 8', dataIndex: 'address', key: '8' },
  {
    title: 'Action',
    key: 'operation',
    fixed: 'right',
    width: 100,
    scopedSlots: { customRender: 'action' },
  },
];

const data = [];
for (let i = 0; i < 100; i++) {
  data.push({
    key: i,
    name: `Edrward ${i}`,
    age: 32,
    address: `London Park no. ${i}`,
  });
}

export default {
  data() {
    return {
      data,
      columns,
    };
  },
  mounted(){
  },
  directives:{
    'mScroll': {
      bind(el, binding){
        const scrollEl = el.querySelector(binding.value);
        function handleScroll(e){
          console.log(e);
        }
        console.log(scrollEl)
        if(scrollEl){
          scrollEl.addEventListener('scroll', handleScroll);
          el.__handleScroll = handleScroll;
        }
        
      },
      unbind(el,binding){
        const scrollEl = el.querySelector(binding.value);
        if(scrollEl &&  el.__handleScroll){
          scrollEl.removeEventListener('scroll', el.__handleScroll);
        }
        
      }
    }
  }
};
</script>
