<template>
  <div class="home">
    <Diagram :moduleData="moduleData" />
  </div>
</template>

<script>
// @ is an alias to /src
import Diagram from "@/components/Diagram";

export default {
  name: "Home",
  components: {
    Diagram
  },
  data() {
    return {
      moduleData: [
        {
          key: "1",
          mission: "任务名称1任务名称1任务名称1",
          totalTel: "4556677",
          nodeId: "2220",
          totalNum: "24",
          category: "total"
        },
        {
          key: "2",
          parent: "1",
          name: "Demeter",
          tel: "13844556678",
          id: "2202220222202220",
          linkNum: "24人"
        },
        {
          key: "3",
          parent: "1",
          name: "Copricat",
          tel: "13844556679",
          id: "2202220222202220",
          linkNum: "24人"
        },
        {
          key: "4",
          parent: "1",
          name: "Jellylorum",
          tel: "13844556680",
          id: "2202220222202220",
          linkNum: "24人"
        },
        {
          key: "5",
          parent: "1",
          name: "Alonzo",
          tel: "13844556681",
          id: "2202220222202220",
          linkNum: "24人"
        },
        {
          key: "6",
          parent: "1",
          name: "Alonzo",
          tel: "13844556682",
          id: "2202220222202220",
          linkNum: "24人"
        },
        {
          key: "7",
          parent: "1",
          name: "Alonzo",
          tel: "13844556683",
          id: "2202220222202220",
          linkNum: "24人"
        },
        {
          key: "8",
          parent: "2",
          name: "Munkustrap",
          tel: "13844556684",
          id: "2202220222202220",
          linkNum: "24人"
        },
        {
          key: "9",
          parent: "2",
          name: "Munkustrap",
          tel: "13844556685",
          id: "2202220222202220",
          linkNum: "24人"
        },
        {
          key: "10",
          parent: "2",
          name: "Munkustrap",
          tel: "13844556686",
          id: "2202220222202220",
          linkNum: "24人"
        },
        {
          key: "11",
          parent: "2",
          name: "Munkustrap",
          tel: "13844556687",
          id: "2202220222202220",
          linkNum: "24人"
        },
        {
          key: "12",
          parent: "2",
          name: "Munkustrap",
          tel: "13844556688",
          id: "2202220222202220",
          linkNum: "24人"
        },
        {
          key: "13",
          parent: "2",
          name: "Munkustrap",
          tel: "13844556689",
          id: "2202220222202220",
          linkNum: "24人"
        }
      ]
    };
  }
};
</script>
