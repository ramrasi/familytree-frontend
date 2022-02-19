<template>
    <h1>Orientation</h1>
    <select v-model="treeOrientation">
        <option value="0">Vertical</option>
        <option value="1">Horizontal</option>
    </select>
    <div class="center">
        <blocks-tree :data="treeData" :horizontal="treeOrientation=='1'" :collapsable="true"></blocks-tree>
    </div>
</template>

<script>
import { defineComponent,ref,reactive } from 'vue';

export default defineComponent({

    setup() {

        let selected = ref([]);
        let treeOrientation = ref("0");
        let treeData = reactive({
            label: 'root',
            expand: true,
            some_id: 1,
            children: [
                { label: 'child 1', some_id: 2, },
                { label: 'child 2', some_id: 3, },
                { 
                    label: 'subparent 1', 
                    some_id: 4, 
                    expand: false, 
                    children: [
                        { label: 'subchild 1', some_id: 5 },
                        {  
                            label: 'subchild 2', 
                            some_id: 6, 
                            expand: false, 
                            children: [
                                { label: 'subchild 11', some_id: 7 },
                                { label: 'subchild 22', some_id: 8 },
                            ]
                        },
                    ]
                },
            ]
        });

        return {
            treeData,
            selected,
            treeOrientation
        }
    }
})

</script>
<style scoped>
.center {
  margin: auto;
  width: 50%;
  /* background-color: red; */
  /* border-style: dashed;  */
}
</style>