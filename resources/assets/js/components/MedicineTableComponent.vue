
<template>
    <data-tables 
               :data='medicines'
               :actions-def='getActionsDef()'
               :checkbox-filter-def='getCheckFilterDef()'
               :row-action-def='getRowActionsDef()'
               >
                   
    <el-table-column prop="barcode" label="Barcode." sortable="custom"></el-table-column>
    <el-table-column prop="name" label="ชื่อ" sortable="custom"></el-table-column>
    <el-table-column prop="ingredient" label="ตัวยาสำคัญและปริมาณ" sortable="custom"></el-table-column>
    <el-table-column prop="category" label="กลุ่มยา" sortable="custom"></el-table-column>
    <el-table-column prop="type" label="รูปแบบยา" sortable="custom"></el-table-column>
    <el-table-column prop="for" label="ใช้เพื่อ" sortable="custom"></el-table-column>
    <el-table-column prop="method" label="วิธีใช้" sortable="custom"></el-table-column>
    <el-table-column prop="notice" label="ข้อควรระวัง" sortable="custom"></el-table-column>
    <el-table-column prop="keeping" label="การเก็บรักษา" sortable="custom"></el-table-column>
    <el-table-column prop="forget" label="กรณียืมใช้ยา" sortable="custom" :width="500"></el-table-column>
  </data-tables>
</template>



<script>
export default {
  props: ["medicines"],
  data() {
    return {
      tableData: []
    };
  },
  created() {
   
  },
  methods: {
    getActionsDef() {
      let self = this;
      return {
        width: 5,
        def: [
          {
            name: "new",
            handler() {
              self.$message("new clicked");
            },
            icon: "plus"
          },
          {
            name: "import",
            handler() {
              self.$message("import clicked");
            },
            icon: "upload"
          }
        ]
      };
    },
    getCheckFilterDef() {
      return {
        width: 14,
        props: "state_code",
        def: [
        //   {
        //     code: "created",
        //     name: "Created"
        //   },
        //   {
        //     code: "assigned",
        //     name: "Assigned"
        //   },
        //   {
        //     code: "accepted",
        //     name: "Accepted"
        //   },
        //   {
        //     code: "closed",
        //     name: "Closed"
        //   },
        //   {
        //     code: "cancelled",
        //     name: "Cancelled"
        //   }
        ]
      };
    },
    getRowActionsDef() {
      let self = this;
      return [
        {
          type: "primary",
          handler(row) {
            self.$message("Edit clicked");
            console.log("Edit in row clicked", row);
          },
          name: "Edit"
        },
        {
          type: "primary",
          handler(row) {
            self.$message("RUA in row clicked");
            console.log("RUA in row clicked", row);
          },
          name: "RUA"
        }
      ];
    }
  }
};
</script>
